# claude-statusline

[![npm version](https://img.shields.io/npm/v/@camkeith/claude-statusline)](https://www.npmjs.com/package/@camkeith/claude-statusline)
[![npm downloads](https://img.shields.io/npm/dm/@camkeith/claude-statusline)](https://www.npmjs.com/package/@camkeith/claude-statusline)
[![license](https://img.shields.io/npm/l/@camkeith/claude-statusline)](./LICENSE)

A width-adaptive status line for Claude Code that shows model, context usage, rate limits, git info, and extra usage budget. Automatically adjusts its layout based on available terminal width.

![Full layout](https://raw.githubusercontent.com/camkeith/claude-statusline/main/.github/screenshot-full.png)

## Install

```bash
npx @camkeith/claude-statusline
```

Backs up your existing status line script and settings, copies the new script to `~/.claude/statusline.sh`, and configures your Claude Code settings.

Requires [jq](https://jqlang.github.io/jq/) for JSON parsing (curl and git are typically preinstalled):

```bash
brew install jq        # macOS
sudo apt install jq    # Debian/Ubuntu
```

## Features

- Catppuccin Macchiato color theme
- Background-colored gauge bars (no Unicode width glitches)
- Git branch and diff stats (modified, added, deleted files)
- Context window usage with color-coded thresholds
- 5-hour and weekly rate limit tracking with reset times
- Extra usage budget shown as "$X left"
- Model name with context window size
- Project name with smart truncation for long names
- Multi-terminal-safe cached API calls (60s TTL, atomic writes, lock-based deduplication)

## Layouts

Adapts to terminal width automatically:

### Full (wide terminals, 2 lines)

Project name, branch, diffs, full model name, context gauge bar, usage gauges with reset times, and extra budget.

![Full layout](https://raw.githubusercontent.com/camkeith/claude-statusline/main/.github/screenshot-full.png)

### Compact (narrower terminals, 2 lines)

Truncated project name, tiny model, context gauge bar, and abbreviated usage gauges.

![Compact layout](https://raw.githubusercontent.com/camkeith/claude-statusline/main/.github/screenshot-compact.png)

### Narrow (small terminals, 1 line)

Short project name, tiny model, color-coded percentages with dividers.

![Narrow layout](https://raw.githubusercontent.com/camkeith/claude-statusline/main/.github/screenshot-narrow.png)

### Ultracompact (smallest terminals, 1 line)

Branch, model, and percentages with no dividers.

![Ultracompact layout](https://raw.githubusercontent.com/camkeith/claude-statusline/main/.github/screenshot-ultracompact.png)

## Uninstall

```bash
npx @camkeith/claude-statusline --uninstall
```

Restores your previous status line script and settings from backup. If there was no previous status line, it removes the script and cleans up settings.

## License

MIT
