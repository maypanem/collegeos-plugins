# Releasing CollegeOS for Claude

## Endpoint

The package connects to `https://collegeos.app/api/claude/mcp`. It serves the
same tools and server instructions as `https://collegeos.app/api/family-guide/mcp`,
with one difference in how a private tool call without a valid token is
answered:

- Claude starts sign-in only when the HTTP request itself fails with
  `401 Unauthorized` and a `WWW-Authenticate: Bearer … resource_metadata=…`
  header. The Claude route answers a private `tools/call` that has a missing,
  expired or invalid token that way, before the MCP server runs. `initialize`,
  `tools/list`, resource reads and the public tools stay anonymous.
- `/api/family-guide/mcp` keeps ChatGPT's contract: an HTTP 200 tool result
  whose `_meta["mcp/www_authenticate"]` carries the challenge. ChatGPT links per
  tool from that result, and Claude ignores it.

Consent, student and permission refusals for a valid token stay ordinary tool
results on both routes, so a revoked or narrowed connection never loops back
into sign-in. The Claude route has its own protected-resource metadata at
`https://collegeos.app/.well-known/oauth-protected-resource/api/claude/mcp`;
its `resource` must equal the endpoint exactly.

The `collegeos` and `setup` skills mirror `plugins/collegeos/skills`. Refresh
both copies together with any change to the shared workflow; the build checks
that they are byte-identical.

## Build and validate

From the application repository:

```sh
npx vitest run tests/lib/collegeos-claude-plugin-package.test.ts
npx tsx scripts/build-collegeos-claude-plugin.ts --output /absolute/path/collegeos-claude-<version>.zip
claude plugin validate --strict ./plugins/collegeos-claude
```

The builder refuses an existing output path, prints the ZIP's SHA-256 and
produces the same bytes for the same sources. The ZIP holds this folder's files
at its root: the manifest at `.claude-plugin/plugin.json` (the only file in
that folder), the connection in `.mcp.json` with Claude's `http` transport,
and the listing icon that the manifest's `icon` field names. It contains no `.app.json`,
`agents/openai.yaml` or OpenAI manifest extensions. Raise `version` in
`plugin.json` for every release.

## Distribution repository

The directory reads the plugin from GitHub, not from the ZIP. Publish only this
folder, never the private application repository:

- Repository `maypanem/collegeos-plugins`, folder `claude/`. It must be public
  before the listing goes live; `documentationUrl` points at its
  `claude/README.md` on `main`.
- Copy the exact built files into `claude/` through a pull request and merge it
  to `main`.
- The developer portal tracks the stable branch **`claude-release`**. Move that
  branch to the merged commit for each release, so the portal needs no edit
  per version.
- Tag the same commit **`claude-vX.Y.Z`** as an immutable receipt. Never move or
  reuse a tag; a corrected release gets a new version.
- Keep **auto-publish off**. A reviewer approves each version, and publishing
  is a deliberate step.

## Release steps

1. Deploy the application and confirm the commit at
   `https://collegeos.app/api/public/version`. Run
   `npx tsx scripts/probe-collegeos-mcp.ts --base https://collegeos.app --route claude --out <file>`
   and keep the receipt.
2. Upload the ZIP to a test Claude account (Customize → Plugins → Upload) and
   run the acceptance matrix in `docs/runbooks/claude-directory-release.md`.
   Do not infer a Claude result from another host's test.
3. Update `claude/` in the distribution repository, then move
   `claude-release` and create the `claude-vX.Y.Z` tag on the same commit.
4. In the portal, validate on that exact tracked commit. Any later push to
   `claude-release` needs a fresh validation before submitting.
5. The connector listing's server URL must equal the `url` in `.mcp.json`.
   Submit the connector and the plugin from the same organization and pair the
   listings.
6. A local validation or an uploaded package is not directory approval. Record
   the app commit, distribution commit, version, ZIP SHA-256 and portal
   statuses in the runbook's receipts table.

There is no marketplace for this plugin, so the README has no marketplace
install line. A version that fails review leaves the published one live. To
roll back a published version, restore the previous release's files in
`claude/` under a higher version number and release that through the same
steps; tags stay where they are.

The package itself does not run a background process, deploy the application,
register OAuth clients, grant family access, submit to a directory or enable
billing.

References checked October 14, 2026:

- [Plugin structure and testing](https://claude.com/docs/plugins/build)
- [Plugin submission](https://claude.com/docs/plugins/submit)
- [Plugin pre-submission checklist](https://claude.com/docs/plugins/pre-submission-checklist)
- [Lazy authentication for connectors](https://claude.com/docs/connectors/building/lazy-authentication)
