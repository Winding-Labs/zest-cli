# Zest CLI

Measure your AI coding sessions with [Zest](https://meetzest.com). One command installs the Zest plugin of each AI coding tool you pick (Claude Code, Codex, Grok Build, Hermes, opencode, Freebuff):

```sh
npx @winding-labs/zest
```

It works on macOS, Linux and Windows (x64) and needs Node.js 18 or newer for the installer only. The CLI itself is a standalone binary in `~/.zest/bin/zest` (`%USERPROFILE%\.zest\bin\zest.exe` on Windows, added to your user PATH — open a new terminal afterwards), verified against SHA256 checksums shipped in the npm package. The CLI's own collector runs only for a tool moved to it with `zest enable` (an opt-in still in testing): it starts with that tool's sessions and stops after the last one closes.

- `zest status` — sign-in, collector and per-tool state
- `zest update` — update now (the CLI also updates itself; set `ZEST_NO_AUTO_UPDATE=1` to turn that off)
- `zest pause` / `zest resume` — stop or restart uploads
- `npx @winding-labs/zest --uninstall` — stop collecting and remove the hooks, shims and the binary

Each plugin signs in once inside its tool; the installer prints the command. `zest enable <tool> --replace-plugin` moves a tool to the CLI instead: it uploads what the plugin still holds and turns it off, so sessions are never collected twice. Only sessions started after setup are collected.

Binaries for each release are attached to this repository's [releases](https://github.com/Winding-Labs/zest-cli/releases).
