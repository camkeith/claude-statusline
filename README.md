# claude-statusline

A width-adaptive status line for Claude Code that shows model, context usage, rate limits, git info, and extra usage budget. Automatically adjusts its layout based on available terminal width.

![demo](./.github/demo.png)

## Layout Tiers

The status line detects your terminal width and picks the best layout:

**Full** (widest terminals, 2 lines)
```
Research paper  main [1M,23A,2D] | Opus 4.6 (1M) | ████████   0%
current ██████ 20% 3pm | weekly ██████  7% 9am, March 19 | extra ██████ $48 left
```

**Wide** (2 lines, abbreviated model name)
```
Research paper  main [1M,23A,2D] | Op 4.6 (1M) | 0%
c ██████ 20% 3pm | w ██████ 7% 9am, 3/19 | ext ██████ $48 left
```

**Compact** (2 lines, truncated project name, tiny model)
```
Research p..  main | Op (1M) | ████████ 0%
c ██████ 20% 3pm | w ██████ 7%
```

**Narrow** (1 line, percentages only)
```
Research p..  main | Op (1M) | 0% | c20% | w7%
```

**Ultracompact** (1 line, no dividers)
```
main Op (1M) 0% c20% w7%
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
- Cached OAuth usage API calls (60s TTL)

## Install

```bash
npx @kamranahmedse/claude-statusline
```

Backs up your existing status line (if any), copies the script to `~/.claude/statusline.sh`, and configures your Claude Code settings.

## Requirements

- [jq](https://jqlang.github.io/jq/) for parsing JSON
- curl for fetching rate limit data
- git for branch info

On macOS:

```bash
brew install jq
```

## Uninstall

```bash
npx @kamranahmedse/claude-statusline --uninstall
```

Restores your previous status line from backup, or removes the script and cleans up settings.

## License

MIT
