# 99tests MCP server and plugin

Order a human-run, real-device test of your app or website from Claude, Cursor, VS Code, Cline, Gemini CLI or any MCP client, and get verified findings back as ready-to-paste fix prompts.

99tests has run crowdsourced testing since 2010: 20,000 registered testers across India on real phones and browsers, fixed prices shown before you pay, and a verified report within days. Docs and pricing: https://99tests.com/mcp-server

## What it does

Your coding agent runs automated tests. 99tests adds what those cannot cover: people using your app on phones, laptops and browsers they own, on real networks. A reviewer verifies every finding before it reaches you.

- The **MCP server** gives the agent five tools: list the packages, create a test job, check its status, fetch the verified report, and show a sample report.
- The **plugin** for Claude and the **extension** for Gemini CLI add guidance on when and how to use those tools: show prices exactly as returned, ask before ordering, hand you the checkout link, and apply the report's fix prompts one at a time.

## Endpoint

Remote server, Streamable HTTP, nothing to install:

```
https://99tests.com/api/mcp
```

## Install

Claude Code plugin (the server plus the `real-device-test` skill):

```
/plugin install 99tests --marketplace 99tests/mcp-server
```

On older Claude Code versions, run these two instead:

```
/plugin marketplace add 99tests/mcp-server
/plugin install 99tests@99tests
```

Claude Code, server only:

```
claude mcp add --transport http 99tests https://99tests.com/api/mcp
```

Gemini CLI extension:

```
gemini extensions install https://github.com/99tests/mcp-server
```

Cursor (`mcp.json`):

```json
{
  "mcpServers": {
    "99tests": {
      "url": "https://99tests.com/api/mcp"
    }
  }
}
```

VS Code (`.vscode/mcp.json`):

```json
{
  "servers": {
    "99tests": {
      "type": "http",
      "url": "https://99tests.com/api/mcp"
    }
  }
}
```

Cline (`cline_mcp_settings.json`):

```json
{
  "mcpServers": {
    "99tests": {
      "type": "streamableHttp",
      "url": "https://99tests.com/api/mcp"
    }
  }
}
```

Other MCP clients: add a remote MCP server with the URL above. Notes for AI agents that install it: [llms-install.md](llms-install.md).

## Use it

Ask your agent, for example:

- "List the 99tests packages and tell me which one fits a release check of my Android app on budget phones."
- "Create a Standard 99tests job and give me the checkout link."
- "Check my 99tests job. If the report is ready, apply the fix prompts one by one."
- "Show me a sample 99tests report."

## Tools

| Tool | What it does |
| --- | --- |
| `list_packages` | Lists test packages with scope, device counts and prices |
| `create_test_job` | Creates a test job and returns a browser checkout link |
| `get_job_status` | Returns the job's stage and progress |
| `get_report` | Returns the verified findings for a delivered job, as fix prompts |
| `get_sample_report` | Returns a sample report so an agent can see the output format |

## How a cycle runs

1. The agent calls `create_test_job` with a package and your email address, and gives you a checkout link.
2. You pay in your browser. No account, no sales call. Then you submit the build link or URL, your test cases and the target devices.
3. Testers run the sessions on real devices; a reviewer verifies every finding.
4. `get_report` returns the findings. Each one includes steps, device, OS, screenshots and a fix prompt the agent can act on.

## Data

The server receives only what a tool call carries: the package you choose, the email address you give for the invoice, status link and report, an optional country code, and your job's status link or token. The plugin and the extension send nothing else and store nothing. Your source code and files are not sent. Builds and test cases go to 99tests in the submit step after checkout, not through the agent.

Privacy policy: https://99tests.com/privacy

Terms: https://99tests.com/terms

## Links

- Server docs: https://99tests.com/mcp-server
- Pricing: https://99tests.com/pricing
- Sample report: https://99tests.com/sample-report/
- Free QA tools (website checker, Play Store bug scanner, test case library): https://99tests.com/tools
- India App Quality Report: https://99tests.com/research/india-app-quality-report-q4-2026

## Support

hello@99tests.com · Issues on this repository are welcome for client-compatibility bugs.

## Licence

This repository (docs, manifests and the skill) is MIT licensed. The hosted service is provided under the 99tests client terms: https://99tests.com/terms
