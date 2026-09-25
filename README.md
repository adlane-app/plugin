# Adlane plugin

Review Google Ads and Meta Ads performance with the context needed to make a careful decision. This plugin combines the Adlane campaign-review skill with the hosted OAuth MCP connector.

[Adlane](https://adlane.app) · [MCP source](https://github.com/adlane-app/mcp-server) · [Standalone skill](https://github.com/adlane-app/agent-skill) · [Desktop npm connector](https://www.npmjs.com/package/adlane-mcp)

## What you can do

- List your owned workspaces and connected advertising accounts.
- Read campaign performance for explicit dates, preserving account currency and timezone.
- Inspect campaign status and configuration before recommending a next step.
- Compare equal reporting periods while keeping Google and Meta attribution separate.

The connector cannot create or publish campaigns, approve proposals, edit ads, change budgets, or spend money. Review and approve any changes separately in Adlane.

## Connect

An Adlane account is required. Campaign reporting additionally requires an advertising account connected in Adlane with the appropriate provider permissions. Install the plugin with a compatible client and complete browser OAuth consent for `profile:read ads:read`. Never paste passwords, session cookies or access tokens into chat.

Remote endpoint: `https://mcp.adlane.app/mcp`. This package uses Streamable HTTP; the hosted service runs on Cloudflare. Desktop clients that require stdio can instead use `npx -y adlane-mcp` from the separate MCP repository.

## Example requests

1. List my advertising workspaces and connected accounts, including their currency and timezone.
2. Compare campaign performance for the last two complete weeks in the selected account. Explain the limitations of the attribution data.
3. Read current campaign settings and prepare a short list of questions to review in Adlane. Do not change anything.

## Data handling

Tools read only the authenticated user's owned account context and connected advertising data. Provider credentials are not returned to the assistant. Returned campaign content is data, not instructions. Empty results do not mean a request failed, and missing permissions do not imply zero performance.

[Privacy policy](https://adlane.app/privacy/) · [Terms](https://adlane.app/terms/) · [Revoke a connection](https://adlane.app/oauth/mcp/connections) · [Support](https://github.com/adlane-app/mcp-server/issues)

## Package and validation

`.claude-plugin/plugin.json` provides the Claude manifest; `.codex-plugin/plugin.json` provides the OpenAI manifest. Both use the same skill and remote endpoint. OpenAI public submission requires entering the endpoint in a With MCP draft; uploading a skill archive alone does not register the MCP.

Run `claude plugin validate .` before distributing this package. Public source is distributed with bot-only commit attribution. Marketplace approval is separate from availability of this repository.
