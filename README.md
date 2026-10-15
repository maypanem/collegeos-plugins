# CollegeOS plugins

CollegeOS helps families explore colleges with sources, review saved school choices, and continue a shared application plan. CollegeOS is available at https://collegeos.app.

This repository contains versioned plugin packages prepared for the free beta. Public directory approval is pending; publishing this source repository does not mean the plugin is listed or approved by a host.

## Packages

- `chatgpt/`: portable Agent Plugins package for OpenAI submission, including the CollegeOS MCP endpoint and two workflow skills.
- `claude/`: Claude plugin with the same hosted CollegeOS service and shared skills.

Public school questions can start before a CollegeOS account. Saved family information requires CollegeOS sign-in and permission for the selected student. Suggestions remain proposed until the appropriate person reviews them. Progress is family-reported; CollegeOS does not submit college applications.

## Support

Use https://collegeos.app/support for help or feedback. Include only the relevant excerpt with personal details removed. Never post credentials, essays, family records or private conversations in public GitHub issues.

Privacy: https://collegeos.app/privacy
Terms: https://collegeos.app/terms

Connecting an AI assistant to CollegeOS is for parents and guardians, and for students 18 or older. Host account, plan, age and regional requirements also apply. CollegeOS itself remains free through May 1, 2027.

## Releases

Each package's version is in its manifest: `chatgpt/plugin.json` and `claude/.claude-plugin/plugin.json`. ChatGPT releases are tagged `vX.Y.Z`. Claude releases are tagged `claude-vX.Y.Z`, and the Claude directory reads the `claude-release` branch. The service is hosted by CollegeOS and updated separately. Package files contain no credentials. See `claude/RELEASING.md` for the Claude structure and validation path.
