# Zest CLI

Measure your AI coding sessions with [Zest](https://meetzest.com). One command installs the Zest plugin of each AI coding tool you pick (Claude Code, Codex, Grok Build, Hermes, opencode, Freebuff):

```sh
npx @winding-labs/zest
```

In a terminal it runs as a short guided setup: pick your tools (the ones found on your machine are preselected) and it installs their plugins. Skip the questions with:

- `--yes` — install the plugins of the detected tools without asking
- `--only=claude,codex,grok,hermes,opencode,freebuff` — install only the tools you list

It works on macOS, Linux and Windows (x64) and needs Node.js 18 or newer for the installer only. The CLI itself is a standalone binary in `~/.zest/bin/zest` (`%USERPROFILE%\.zest\bin\zest.exe` on Windows, added to your user PATH — open a new terminal afterwards), verified against SHA256 checksums shipped in the npm package.

Each plugin signs in once inside its tool; the installer prints the command. Only sessions started after setup are collected.

- `zest status` — your Zest plugins per tool: sign-in, sync, last sync and errors; `--watch` keeps it live, `--json` prints it as JSON
- `zest update` — install the latest release
- `zest pause` / `zest resume` — stop or restart uploads
- `zest logout` — sign this device out, also on the Zest server; the web app, your plugins and other devices stay signed in
- `npx @winding-labs/zest --uninstall` — stop collecting, remove the hooks, shims and the binary and sign out; the Zest plugins stay installed (it offers to turn back on any plugin the CLI replaced)

`zest enable <tool> --replace-plugin` moves a tool from its plugin to the CLI's own collector. That is an invite-only test: without it the command switches nothing. Where it is on, the CLI also updates itself; set `ZEST_NO_AUTO_UPDATE=1` to turn that off.

Binaries for each release are attached to this repository's [releases](https://github.com/Winding-Labs/zest-cli/releases).
