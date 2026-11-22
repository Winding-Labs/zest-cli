# Zest CLI

Measure your AI coding sessions with [Zest](https://meetzest.com/?utm_source=npmjs.com&utm_medium=referral&utm_campaign=npm-readme), a usage tracker and dashboard for Claude Code, Codex and the other coding agents your team runs. One command installs the Zest plugin of each AI coding tool you pick (Claude Code, Codex, Grok Build, Hermes, opencode, Freebuff):

```sh
npx @winding-labs/zest
```

In a terminal it runs as a short guided setup: pick your tools (the ones found on your machine are preselected) and it installs their plugins. Skip the questions with:

- `--yes` — install the plugins of the detected tools without asking
- `--only=claude,codex,grok,hermes,opencode,freebuff` — install only the tools you list

It works on macOS, Linux and Windows (x64) and needs Node.js 18 or newer for the installer only. The CLI itself is a standalone binary in `~/.zest/bin/zest` (`%USERPROFILE%\.zest\bin\zest.exe` on Windows, added to your user PATH — open a new terminal afterwards), verified against SHA256 checksums shipped in the npm package.

Then it opens your browser with a sign-in code filled in: one Approve signs in every plugin it installed. Without a terminal it prints `zest login` instead, which does the same. Only sessions started after setup are collected.

- `zest status` — your Zest plugins per tool: sign-in, sync, last sync and errors; `--watch` keeps it live, `--json` prints it as JSON
- `zest login` — sign in once, for the CLI and every installed plugin that is not signed in yet
- `zest update` — install the newest release
- `zest pause` / `zest resume` — stop or restart uploads
- `zest logout` — sign this device out, also on the Zest server; the web app, your plugins and other devices stay signed in
- `npx @winding-labs/zest --uninstall` — take the Zest plugin off every coding agent and sign them out, stop collecting, remove the hooks, shims and the binary; `--only=claude,grok` takes Zest off just those agents

`zest enable <tool> --replace-plugin` moves a tool from its plugin to the CLI's own collector. That is an invite-only test: without it the command switches nothing. Where it is on, the CLI also updates itself; set `ZEST_NO_AUTO_UPDATE=1` to turn that off.

The installer sends two anonymous events to PostHog, when the install starts and when it ends: the CLI version, your OS and architecture, the tools it found and picked, and how each install went. They carry a random id kept in `~/.zest/collector`, never your account, paths or machine name; PostHog reads a rough location from the connection. Set `DO_NOT_TRACK=1` or `ZEST_TELEMETRY=0` to turn them off; nothing is sent when `CI=true`.

Binaries for each release are attached to this repository's [releases](https://github.com/Winding-Labs/zest-cli/releases).
