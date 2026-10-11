# Releasing CollegeOS for Claude

The `collegeos` and `setup` skills mirror `plugins/collegeos/skills`. Refresh
both copies together with any change to the shared workflow. The build verifies
their exact contents. The Claude package uses the same hosted endpoint as the
other CollegeOS integration and requests no extra account access.

From the application repository, run:

```sh
npx vitest run tests/lib/collegeos-claude-plugin-package.test.ts
npx tsx scripts/build-collegeos-claude-plugin.ts --output /tmp/collegeos-claude.zip
claude plugin validate ./plugins/collegeos-claude
```

The ZIP contains this folder's files directly. Its manifest is at
`.claude-plugin/plugin.json` and the remote connection is in `.mcp.json` with
Claude's `http` transport. It includes no `.app.json`, `agents/openai.yaml`, or
OpenAI manifest extensions.

## Publication and testing

1. Upload the ZIP to a test Claude account. Confirm the skills load and connect
   CollegeOS through its Connectors tab. Run ordinary public exploration,
   authorized shortlist and comparison reads, and saved-plan resumption.
2. Check denied access, wrong student/account, cancellation, and revoked
   access. Do not infer a successful Claude journey from another host's test.
   Operator or synthetic accounts can verify the free beta before publication;
   independent-family feedback follows launch.
3. For directory publication, copy only this folder into a dedicated
   distribution repository. Do not publish the private application repository
   to distribute the plugin. This bundle's limited license does not license the
   backend or customer data.
4. Connect a GitHub account with write access in the Claude developer portal,
   validate the exact plugin commit, and complete its data-handling information
   from the actual service policies. Submit the hosted MCP server separately
   as a connector and keep the URL identical to `.mcp.json`.
5. Review the portal's results and publish the passing version. A completed
   local validation is not directory approval or a public listing. Add the
   actual marketplace install command to the README only if a marketplace is
   also configured. Increase the plugin version on subsequent releases.

The package itself does not run a background process, deploy the application,
register OAuth clients, grant family access, submit to a directory, or enable
billing. Its build output is an artifact for the operator to validate and
release. ChatGPT can launch independently while this verification is pending.

References checked October 11, 2026:

- [Plugin structure and testing](https://claude.com/docs/plugins/build)
- [Plugin submission](https://claude.com/docs/plugins/submit)
- [Plugin pre-submission checklist](https://claude.com/docs/plugins/pre-submission-checklist)
