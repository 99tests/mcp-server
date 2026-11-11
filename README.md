# 99tests MCP server

Order a human-run, real-device test of your app or website from Claude Code, Cursor, VS Code or any MCP client, and get verified findings back as ready-to-paste fix prompts.

99tests has run crowdsourced testing since 2010: 20,000 registered testers across India on real phones and browsers, fixed prices from $129 per test cycle, a verified report in 3 days. Docs and pricing: https://99tests.com/mcp-server

## Endpoint

Remote server, HTTP transport (Streamable HTTP), no install:

```
https://99tests.com/api/mcp
```

## Install

Claude Code:

```
claude mcp add --transport http 99tests https://99tests.com/api/mcp
```

Cursor or VS Code (`mcp.json`):

```json
{
  "mcpServers": {
    "99tests": {
      "url": "https://99tests.com/api/mcp"
    }
  }
}
```

Other MCP clients: add a remote MCP server with the URL above.

## Tools

| Tool | What it does |
| --- | --- |
| `list_packages` | Lists test packages with scope, device counts and prices |
| `create_test_job` | Creates a test job for a build or URL and returns a browser checkout link |
| `get_job_status` | Returns the job state (awaiting payment, testing, verifying, delivered) |
| `get_report` | Returns the verified findings for a delivered job, as fix prompts |
| `get_sample_report` | Returns a sample report so an agent can see the output format |

## How a cycle runs

1. The agent calls `create_test_job` with the build (APK, TestFlight link or URL) and a package.
2. The human pays through the checkout link. No account, no sales call.
3. Testers run the agreed session on real devices; a reviewer verifies every finding.
4. `get_report` returns the findings. Each one includes steps, device, OS, screenshots and a fix prompt the agent can act on.

## Links

- Server docs: https://99tests.com/mcp-server
- Pricing: https://99tests.com/pricing
- Sample report: https://99tests.com/sample-report/
- Free QA tools (website checker, Play Store bug scanner, test case library): https://99tests.com/tools
- India App Quality Report: https://99tests.com/research/india-app-quality-report-q4-2026

## Support

hello@99tests.com · Issues on this repository are welcome for client-compatibility bugs.

## Licence

This repository (docs and manifests) is MIT licensed. The hosted service is provided under the 99tests client terms: https://99tests.com/terms
