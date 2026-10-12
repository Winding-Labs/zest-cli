# Zest CLI

Measure your AI coding sessions with [Zest](https://meetzest.com). One command installs the Zest CLI, signs you in, and collects new Claude Code and Codex sessions in the background:

```sh
npx @winding-labs/zest
```

It works on macOS, Linux and Windows (x64) and needs Node.js 18 or newer for the installer only. The CLI itself is a standalone binary in `~/.zest/bin/zest` (`%USERPROFILE%\.zest\bin\zest.exe` on Windows, added to your user PATH — open a new terminal afterwards), verified against SHA256 checksums shipped in the npm package. The collector starts with each Claude Code and Codex session and stops after the last one closes; `zest start` keeps it running until `zest stop`.

- `zest status` — sign-in, collector and per-tool state
- `zest update` — update now (the CLI also updates itself; set `ZEST_NO_AUTO_UPDATE=1` to turn that off)
- `zest pause` / `zest resume` — stop or restart uploads
- `npx @winding-labs/zest --uninstall` — stop collecting and remove the hooks, shims and the binary

If a tool already has the Zest plugin, the installer uploads what the plugin still holds and turns it off, so sessions are never collected twice. Only sessions started after setup are collected.

Binaries for each release are attached to this repository's [releases](https://github.com/Winding-Labs/zest-cli/releases).
