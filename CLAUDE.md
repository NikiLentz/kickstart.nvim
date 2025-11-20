# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Neovim configuration based on Kickstart.nvim - a minimal, single-file Neovim setup written in Lua. The configuration is intentionally kept simple and fully documented to serve as a learning tool and starting point for customization.

## Architecture

### Configuration Structure

- **init.lua**: Main configuration file containing all settings, keymaps, autocommands, and plugin specifications (lines 87-1058)
- **lua/kickstart/plugins/**: Optional modular plugins from Kickstart
  - neo-tree.lua: File browser plugin
  - Other plugins (autopairs, debug, gitsigns, indent_line, lint) are available but commented out
- **lua/custom/plugins/**: Directory for user's own custom plugins (currently empty)

### Plugin Management

Uses [lazy.nvim](https://github.com/folke/lazy.nvim) as the plugin manager (initialized at line 235-246). Plugins are configured in the `require('lazy').setup()` call starting at line 259.

### Key Plugin Categories

1. **LSP & Completion**:
   - nvim-lspconfig: LSP client configuration (lines 507-767)
   - mason.nvim: Automatic LSP/tool installer (line 514)
   - mason-lspconfig.nvim: Bridges Mason and lspconfig
   - blink.cmp: Autocompletion engine (lines 817-913)
   - LuaSnip: Snippet engine

2. **Fuzzy Finding**:
   - telescope.nvim: Fuzzy finder for files, LSP symbols, grep, etc. (lines 385-492)
   - telescope-fzf-native.nvim: Native FZF sorter for better performance

3. **Code Intelligence**:
   - nvim-treesitter: Syntax highlighting and code understanding (lines 983-1006)
   - conform.nvim: Autoformatting (lines 770-815)

4. **UI/UX**:
   - which-key.nvim: Shows pending keybinds (lines 325-376)
   - neo-tree.nvim: File explorer (toggled with `\`)
   - mini.nvim: Collection of small utilities (statusline, surround, text objects) (lines 946-982)
   - catppuccin: Color scheme (lines 916-930)

5. **Git**:
   - gitsigns.nvim: Git decorations in gutter (lines 284-295)

6. **AI Assistance**:
   - copilot.vim: GitHub Copilot integration (lines 932-940)

7. **Session Management**:
   - auto-session: Automatic session save/restore (lines 297-310)

## Important Configuration Details

### Leader Key
Space is set as the leader key (`vim.g.mapleader = ' '`) at line 90. This must be set before plugins load.

### LSP Configuration
- LSP servers are defined in the `servers` table (lines 702-730)
- Currently configured: `ts_ls` (TypeScript), `lua_ls` (Lua)
- Capabilities are extended by blink.cmp for better completion (line 691)
- LSP keymaps are set on LspAttach autocmd (lines 554-656)

### Formatting
- Conform.nvim handles formatting (lines 770-815)
- Format on save is enabled for most filetypes except C/C++
- JavaScript/TypeScript use eslint_d formatter
- Lua uses stylua formatter
- Manual format keymap: `<leader>f`

### Key Custom Settings
- Tab settings: 2 spaces, expand tabs (lines 108-111)
- Relative line numbers enabled (line 106)
- Clipboard synced with OS (line 124)
- Confirm before quitting with unsaved changes (line 173)
- Telescope ignores node_modules (lines 441-443)

## Common Commands

### Plugin Management
```vim
:Lazy              " View plugin status
:Lazy update       " Update all plugins
:Lazy sync         " Install missing and update plugins
```

### LSP
```vim
:Mason             " Open Mason installer UI
:LspInfo           " Show LSP client info for current buffer
:checkhealth       " Check Neovim health (dependencies, LSP, etc.)
```

### Formatting
```vim
:ConformInfo       " Show formatter info for current buffer
```

### Key Keymaps

**Navigation**:
- `<C-h/j/k/l>`: Move between windows
- `=/−`: Resize windows vertically
- `+/_`: Resize windows horizontally
- `\`: Toggle Neo-tree file explorer

**Telescope (all start with `<leader>s`)**:
- `<leader>sf`: Search files
- `<leader>sg`: Live grep
- `<leader>sw`: Search current word
- `<leader>sh`: Search help
- `<leader>sk`: Search keymaps
- `<leader>sn`: Search Neovim config files
- `<leader>/`: Fuzzy search in current buffer
- `<leader><leader>`: Find existing buffers

**LSP (gr prefix)**:
- `grn`: Rename symbol
- `gra`: Code action
- `grr`: References
- `grd`: Go to definition
- `gri`: Go to implementation
- `grt`: Go to type definition
- `gO`: Document symbols
- `gW`: Workspace symbols

**Formatting**:
- `<leader>f`: Format current buffer

## Development Workflow

1. **Installing Tools**: Use `:Mason` to install LSP servers, formatters, and linters
2. **Adding LSP Support**: Add server name to `servers` table in init.lua (line 702)
3. **Adding Formatters**: Add to `formatters_by_ft` in conform config (line 807)
4. **Adding Plugins**: Add plugin specs to the `require('lazy').setup()` call or create files in `lua/custom/plugins/`
5. **Custom Keymaps**: Add to init.lua or in plugin configs

## File Locations

- Config directory: `~/.config/nvim` (macOS/Linux)
- Plugin data: `~/.local/share/nvim/`
- Sessions: `~/.local/share/nvim/sessions/`
- Lazy.nvim plugin cache: `~/.local/share/nvim/lazy/`

## Notes

- This config is designed to be readable and self-documenting - read through init.lua to understand what each section does
- The philosophy is to keep everything in one file initially, then modularize as needed
- Nerd Font is recommended but optional (controlled by `vim.g.have_nerd_font` at line 94)
- Auto-session will automatically save/restore sessions when opening Neovim in a directory
