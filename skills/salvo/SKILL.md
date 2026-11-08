---
name: salvo
description: Run a job search through Salvo (sendsalvo.com) from an AI agent. Check applications and interviews, get interview prep, pause or resume the search, change target titles, and send one job link for Salvo to apply to. Use when the user asks about their Salvo account, their job applications, or wants Salvo to apply to a job.
license: MIT
metadata:
  homepage: https://sendsalvo.com
---

# Salvo

[Salvo](https://sendsalvo.com) finds jobs that fit a person, applies with a resume rewritten for each job, and preps them for interviews. This skill lets an agent work with one person's own Salvo account through Salvo's hosted MCP server.

The user needs a Salvo account first. If they don't have one, send them to https://sendsalvo.com/start. Salvo is free until the 2nd interview request and needs no card. Current prices are at https://sendsalvo.com/salvo-is-it-free.html.

## Connect

The server address is `https://sendsalvo.com/mcp`. It uses OAuth: the user signs in with their Salvo email and a six-digit code. Never ask the user to paste the code into chat.

Claude Code:

```bash
claude mcp add --transport http salvo https://sendsalvo.com/mcp
```

Then run `/mcp`, pick salvo and choose Authenticate.

Other apps, including claude.ai, ChatGPT and Codex: follow https://sendsalvo.com/connect.html.

## Tools

Read only:

- `get_status`: how the search is going.
- `list_applications`: the user's applications.
- `get_application`: one application in detail.
- `list_interviews`: interview requests.
- `get_interview_prep`: prep for one interview.
- `ask_about_job`: what Salvo knows about one job for this user.
- `get_referral_link`: the user's referral link.

These change the account:

- `pause_search` and `resume_search`: stop or restart applying.
- `add_target_titles` and `remove_target_titles`: edit the list of job titles.
- `update_criteria`: replaces the search rules.
- `apply_to_job`: asks Salvo to apply to one job link.

## Rules for the agent

- Confirm with the user before `apply_to_job` or `update_criteria`. An application can't be taken back.
- To add or remove a title, use `add_target_titles` or `remove_target_titles`. `update_criteria` replaces the whole list.
- Report what the tools return. Don't guess an application's status, and don't promise an interview.
- The server only shows the signed-in person's data and can't delete anything.
