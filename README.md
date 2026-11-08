# Salvo agent skill and plugin

Use [Salvo](https://sendsalvo.com) from your AI agent. Salvo finds jobs that fit you, applies with a resume rewritten for each job, and preps you for interviews. This package connects an agent to your own account so you can check applications, see interviews, pause the search, change titles, or send it a job link.

You need a Salvo account: [start here](https://sendsalvo.com/start).

## Install

Skill for Claude Code, Cursor, Codex and others:

```bash
npx skills add markosdaget/salvo-agent --skill salvo
```

Setup for every other app is at [sendsalvo.com/connect](https://sendsalvo.com/connect.html).

## What this package does

It's configuration only: a skill file and the address of Salvo's hosted server. There's no code to run, no API key and no telemetry from this package.

Before you install, know this:

- Every tool call goes to `https://sendsalvo.com/mcp`, Salvo's server.
- Hermes uses `mcp-remote` through `npx` to reach that server, and it opens a browser once so you can sign in with your Salvo email and a six-digit code. That sign-in needs a person, so it won't finish in an unattended run.
- Your login is stored by your agent app or `mcp-remote`, on your machine.
- `apply_to_job` sends a real job application from your account, and it can't be taken back. `update_criteria` replaces your search rules.
- The server shows only the signed-in person's data and has no delete tool.

## License

MIT
