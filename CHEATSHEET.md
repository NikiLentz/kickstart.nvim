# Neovim Cheat Sheet

## Basic Movement & Navigation

| Key | Action | Key | Action | Key | Action |
|-----|--------|-----|--------|-----|--------|
| `h/j/k/l` | Left/Down/Up/Right | `w` | Next word start | `b` | Previous word start |
| `e` | Next word end | `0` | Line start | `$` | Line end |
| `^` | First non-blank char | `gg` | File start | `G` | File end |
| `{` | Previous paragraph | `}` | Next paragraph | `%` | Jump to matching bracket |
| `<C-u>` | Half page up | `<C-d>` | Half page down | `<C-o>` | Jump back |
| `<C-i>` | Jump forward | `f{char}` | Find char forward | `t{char}` | Till char forward |

## Editing & Text Manipulation

| Key | Action | Key | Action | Key | Action |
|-----|--------|-----|--------|-----|--------|
| `i` | Insert before cursor | `a` | Insert after cursor | `I` | Insert at line start |
| `A` | Insert at line end | `o` | New line below | `O` | New line above |
| `x` | Delete character | `dd` | Delete line | `D` | Delete to line end |
| `yy` | Copy line | `p` | Paste after | `P` | Paste before |
| `u` | Undo | `<C-r>` | Redo | `.` | Repeat last change |
| `>>` | Indent line | `<<` | Unindent line | `J` | Join lines |
| `~` | Toggle case | `gU` | Uppercase | `gu` | Lowercase |

## Text Objects & Surround (mini.surround)

| Key | Action | Key | Action | Key | Action |
|-----|--------|-----|--------|-----|--------|
| `ciw` | Change inner word | `ci"` | Change inside quotes | `ci(` | Change inside parentheses |
| `ci{` | Change inside braces | `ci[` | Change inside brackets | `cit` | Change inside HTML tag |
| `viw` | Select inner word | `vi"` | Select inside quotes | `vi(` | Select inside parentheses |
| `va"` | Select around quotes | `va(` | Select around parens | `va{` | Select around braces |
| `saiw)` | Surround word with () | `sd"` | Delete surrounding quotes | `sr)"` | Replace () with "" |

## Windows & Splits

| Key | Action | Key | Action | Key | Action |
|-----|--------|-----|--------|-----|--------|
| `<C-h>` | Focus left window | `<C-j>` | Focus down window | `<C-k>` | Focus up window |
| `<C-l>` | Focus right window | `=` | Increase width | `-` | Decrease width |
| `+` | Increase height | `_` | Decrease height | `<C-w>s` | Split horizontal |
| `<C-w>v` | Split vertical | `<C-w>q` | Close window | `<C-w>=` | Equal size windows |

## File Explorer & Search

| Key | Action | Key | Action |
|-----|--------|-----|--------|
| `\` | Toggle Neo-tree | `<Space>sf` | **Find files** |
| `<Space>sg` | **Grep search** (live) | `<Space>sw` | Search word under cursor |
| `<Space>sh` | Search help | `<Space>sk` | Search keymaps |
| `<Space>sd` | Search diagnostics | `<Space>sr` | Resume last search |
| `<Space>s.` | Recent files | `<Space>sn` | Search Neovim config |
| `<Space>s/` | Grep in open files | `<Space>/` | Search in current buffer |
| `<Space><Space>` | **Find open buffers** | `<Esc>` | Clear search highlight |

## LSP & Code Navigation

| Key | Action | Key | Action |
|-----|--------|-----|--------|
| `grn` | **Rename symbol** | `gra` | **Code action** |
| `grd` | **Go to definition** | `grr` | Find references |
| `gri` | Go to implementation | `grt` | Go to type definition |
| `grD` | Go to declaration | `gO` | Document symbols (outline) |
| `gW` | Workspace symbols | `K` | Hover documentation |
| `<Space>f` | **Format buffer** | `<Space>th` | Toggle inlay hints |

## Diagnostics & Visual Mode

| Key | Action | Key | Action | Key | Action |
|-----|--------|-----|--------|-----|--------|
| `<Space>q` | Diagnostic quickfix | `[d` | Previous diagnostic | `]d` | Next diagnostic |
| `v` | Enter visual mode | `V` | Visual line mode | `<C-v>` | Visual block mode |
| `>` | Indent selection | `<` | Unindent selection | `y` | Yank (copy) |
| `d` | Delete selection | `c` | Change selection | `~` | Toggle case |

## Modes & Search

| Key | Action | Key | Action | Key | Action |
|-----|--------|-----|--------|-----|--------|
| `<Esc>` | Normal mode / Clear | `:` | Command mode | `/` | Search forward |
| `?` | Search backward | `n` | Next search result | `N` | Previous search result |
| `<Esc><Esc>` | Exit terminal mode | `<C-w>` (cmd) | Delete word back | `<C-u>` (cmd) | Clear line |

## Auto-completion (blink.cmp)

| Key | Action | Key | Action | Key | Action |
|-----|--------|-----|--------|-----|--------|
| `<C-Space>` | Open completion menu | `<C-n>` | Next item | `<C-p>` | Previous item |
| `<C-y>` | Accept completion | `<C-e>` | Close menu | `<C-k>` | Toggle signature help |
| `<Tab>` | Next snippet field | `<S-Tab>` | Previous snippet field | | |

## Quick Reference

**Leader Key:** `<Space>` • **Nerd Font:** Enabled • **Clipboard:** Synced with system • **Format on Save:** Enabled • **Which-key:** Press `<Space>` and wait 300ms • **Session:** Auto-save/restore • **Copilot:** Enabled • **File Explorer:** `\`

## Most Useful Combos

1. **Find & Edit:** `<Space>sf` → find file, `grd` → jump to definition, `grn` → rename
2. **Search Code:** `<Space>sg` → grep search entire project
3. **Quick Format:** `<Space>f` → format current file
4. **File Tree:** `\` → toggle file explorer
5. **Buffer Switch:** `<Space><Space>` → quickly switch between open files
6. **Code Actions:** `gra` → see available fixes/refactors
7. **Undo Tree:** `u` (undo), `<C-r>` (redo) - persistent across sessions
