# Changelog

All notable changes to this Neovim configuration (forked from [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim)) are documented in this file.

---

## Personal Customizations (jjspscl/kickstart.nvim)

### 2026-03-11 — Multi-language LSP, Neo-tree & VS Code keymaps
- **Multi-language LSP** — Added `tsserver`, `eslint`, `basedpyright`, `ruff`, and `gopls` (with `gofumpt`, `staticcheck`, `unusedparams`) to Mason-managed servers
- **Mason refactor** — Separated LSP server installs (`mason-lspconfig`) from tool installs (`mason-tool-installer`); tools list now includes `stylua`, `prettierd`, `gofumpt`, `goimports`
- **Formatters (conform.nvim)** — Configured `prettierd`/`prettier` for JS/TS/JSON, `ruff_format` for Python, `goimports` + `gofumpt` for Go
- **Neo-tree replaces nvim-tree** — Enabled `kickstart.plugins.neo-tree`; added `<C-b>` VS Code-style sidebar toggle; show dotfiles and gitignored files
- **mini.comment** — Enabled `mini.comment` for `gc` toggle-comment support
- **mini.pairs** — Enabled `mini.pairs` for auto-closing brackets and quotes
- **Telescope `<C-p>`** — Added VS Code-style `<C-p>` keymap for `find_files`
- **Gitsigns extended keymaps** — Enabled `kickstart.plugins.gitsigns` (stage, reset, blame, diff)
- **Treesitter expanded** — Added `css`, `json`, `javascript`, `typescript`, `tsx`, `python`, `go`, `gomod`, `gosum`, `gowork` grammars
- **Arrow keys allowed** — Commented out arrow-key disable hints (arrow keys work normally now)
- **nvim-tree removed** — Replaced by Neo-tree

### 2025-04-28 — `➕ MORE CONFIGS`
- **Transparent background** — Added autocommand group `TransparentBackground` that clears `Normal`, `NormalNC`, `NonText`, and `NormalFloat` backgrounds on every `ColorScheme` event
- **True color** — Enabled `vim.opt.termguicolors`
- **Relative line numbers** — Enabled `vim.opt.relativenumber`
- **WSL clipboard** — Added `vim.g.clipboard` configuration using `clip.exe` / `powershell.exe` for WSL copy/paste
- **Disabled netrw** — Set `vim.g.loaded_netrw` and `vim.g.loaded_netrwPlugin` to disable the built-in file explorer
- **Colorscheme** — Changed active colorscheme from `tokyonight` to `koehler`
- **Tokyonight configured transparent** — Set `transparent = true` and disabled italic comments in tokyonight setup
- **Telescope file ignore** — Added `file_ignore_patterns` for `node_modules/` and `.git/`
- **TypeScript LSP** — Added `ts_ls` to the LSP servers list
- **nvim-tree.lua** — Added file tree explorer plugin with `<leader>e` toggle (30px left sidebar, shows dotfiles and git status)
- **tmux.nvim** — Added `aserowy/tmux.nvim` for tmux copy sync integration
- **copilot.lua** — Added `zbirenbaum/copilot.lua` with inline suggestions (`<C-CR>` to accept) and panel support
- **`vim.opt.confirm`** — Already present from upstream

### 2024-05-25 — `ADD indent lines` / `DEFAULT theme and disable arrows`
- **Indent guides** — Enabled `indent-blankline.nvim` (`kickstart.plugins.indent_line`)
- **Default theme** — Initially set colorscheme to `default` (later changed to `koehler`)

### 2024-05-24 — Merged upstream `nvim-lua:master`

---

## Upstream Kickstart.nvim History

### 2025 (pulled via upstream merge)

#### Completion & LSP
- **blink.cmp replaces nvim-cmp** — Switched from `hrsh7th/nvim-cmp` to `saghen/blink.cmp` for autocompletion with Rust fuzzy matcher support (#1426)
- **Function signature help** — Added `blink.cmp` signature help enabled by default (#1358)
- **LSP keybindings updated** — Changed to Neovim 0.11 `gr`-prefixed defaults: `grn` (rename), `gra` (code action), `grr` (references), `gri` (implementation), `grd` (definition), `grD` (declaration), `gO` (document symbols), `gW` (workspace symbols), `grt` (type definition) (#1427)
- **lazydev.nvim replaces neodev.nvim** — Switched to `folke/lazydev.nvim` with luvit type support (#1303)
- **Diagnostic config** — Added comprehensive `vim.diagnostic.config` with severity sorting, rounded borders, Nerd Font icons, and virtual text formatting (#1335)
- **Prevent double Mason setup** — Fixed Mason being set up twice (#1298)

#### Plugins & UI
- **Telescope branch unlocked** — Removed `0.1.x` branch lock, now tracks latest (#1448)
- **which-key v3** — Migrated to which-key v3 spec format with delay setting (#1022, #1276)
- **conform.nvim** — Made lazy-loadable again with `BufWritePre` event, improved `format_on_save` to return `nil` for disabled filetypes (#977, #1395)
- **Gitsigns** — Fixed deprecated function calls (#1321), consistent visual mode descriptions (#1266)
- **Neo-tree** — Enabled silent keymap option (#1108), fixed description (#932)
- **nvim-dap** — Made lazy-loadable (#978), fixed DAP loading (#1216), added breakpoint icons (#1194)
- **nvim-lint** — Disabled linting for readonly buffers (#1202)

#### Configuration & Quality of Life
- **`vim.opt.confirm = true`** — Added confirmation dialog for unsaved changes (#1384)
- **Deferred clipboard** — Moved clipboard setting to `vim.schedule` for faster startup (#1049)
- **Window movement** — Added commented-out `<C-S-hjkl>` keymaps for moving windows (#1368)
- **`ts_ls` replaces `tsserver`** — Updated TypeScript LSP server name (#1131)
- **Neovim 0.10 updates** — Various compatibility fixes for Neovim 0.10 (#936)
- **Treesitter** — Added `markdown_inline` and `query` to ensure_installed, removed `prefer_git`, added required parsers (#1061, #2df5137)
- **lazy.nvim bootstrap** — Added error handling for bootstrap clone (#1001)
- **`vim.uv` compatibility** — Updated to use `(vim.uv or vim.loop).fs_stat` (#1095)
- **README updates** — Fixed Windows paths to `%localappdata%`, updated admonition syntax, grammar fixes (#963, #1414, #1450)

### 2024-05-10
- Automatically set detached state as needed (#925)

### 2024-05-08
- fix: `debug.lua` — fixed DAP configuration (#918)

### 2024-05-05
- Add `diff` to Treesitter's `ensure_installed` languages (#908)

### 2024-05-02
- Move `LspDetach` handler near `kickstart-lsp-highlight` group (#900)

### 2024-04-27
- README: add clipboard tool dependency (#886)

### 2024-04-22
- Fix highlight group clear on each attach (#874)
- Fix highlight errors when LSP crash or stop (#864)
- Fix deprecation notice of inlay hints (#873)

### 2024-04-20
- Add commented-out example of classic complete keymaps (#868)
- Minor improvements to Debian install instructions (#869)

### 2024-04-19
- fix: restore Mason config timing for DAP startup (#865)

### 2024-04-17 – 2024-04-18
- Move plugin examples from README to optional plugin files (`debug`, `lint`, `autopairs`, `neo-tree`, `gitsigns`) (#831)
- Enable inlay hints for supporting language servers (#843)
- Add `prefer_git` to Treesitter config (#856)
- Add gitsigns recommended keymaps as optional plugin (#858)

### 2024-04-01 – 2024-04-16
- Don't lazy-load `conform.nvim` plugin (#818)
- Add `<leader>f` keymap to format buffer using conform (#817)
- README: restructured install section (#819)
- Pull request template added (#825)
- Arch Linux install recipe (#852)

### 2024-03-15 – 2024-03-27
- conform: disable autoformat on save for specified filetypes (#694)
- Add linter plugin `nvim-lint` (#699)
- Move `friendly-snippets` to LuaSnip dependencies (#759)
- Add `<C-b>`/`<C-f>` cmp mapping to scroll docs (#750)
- Add `nvim-nio` as dependency for `nvim-dap-ui` (#774)
- Fix: disable Treesitter indenting for Ruby
- Added `folke/neodev.nvim` for Neovim API completion (#754)

### 2024-03-04 – 2024-03-12
- feat: allow Treesitter defaults to be overwritten from custom directory (#732)
- Make Nerd Font optional (#716)
- Use `init` for colorscheme loading (#715)
- Change statusline location to `LINE:COLUMN` (#689)
- fix: checkhealth reported nvim version (#685)
- feat: use `VimEnter` event instead of `VeryLazy` (#673)

### 2024-02-26
- **Major rewrite**: slimmer, trimmer, and more lazy `kickstart.nvim` (#635)
  - Migrated to modular lazy.nvim plugin specs
  - Added `which-key.nvim`, `mini.nvim` (ai, surround, statusline)
  - Added `todo-comments.nvim`, `conform.nvim`
  - Streamlined LSP, Treesitter, and completion setup

### 2024-01 – 2024-02
- Add build step to LuaSnip (#611)
- Add hints for new Neovim users (#615)
- Code action contexts (#599)
- Onedark style option (#590)
- Treesitter warnings fix (#582)

### 2023-12
- Restore Mason config timing for DAP startup (#555)
- Path completion feature for nvim-cmp (#536)
- Two essential Telescope keymaps (#528)
- Gitsigns recommended keymaps (#531)
- GitHub Action for Lua formatting (#526)

### 2023-09 – 2023-11
- `fidget.nvim` updated — removed legacy tag (#505)
- Auto-completion: first menu item selected by default (#502)
- Live Grep from Git root (#492, #494)
- FAQ additions: single-file rationale, `NVIM_APPNAME` (#480, #486)
- `indent-blankline` v3 migration (#443, #446)
- Mason setup fixes (#455, #456)
- Deferred Treesitter setup for faster startup

### 2023-04 – 2023-08
- `telescope-fzf-native` made a dependency (#384)
- LSP goto implementation via Telescope (#404)
- Treesitter: ensure JavaScript installed (#410)
- Custom filetypes for language servers (#373)
- Debug keybinding descriptions (#346)
- Treesitter indent for Python (#337)
- LuaSnip locally jumpable (#302)
- `<C-n>`/`<C-p>` mappings for nvim-cmp (#289)
- `dapui.toggle` added (#281)

### 2023-01 – 2023-03
- Migrated from Packer to `lazy.nvim` (#178)
- Clipboard sync by default (#166)
- Diagnostic keymap descriptions (#191)
- `mason-nvim-dap` 2.0 migration (#258)
- Treesitter `:TSInstall` build fix (#261)

### 2022-06 – 2022-12
- **Initial release** — `kickstart.nvim` created
- Core setup: LSP (`nvim-lspconfig`), Treesitter, Telescope, nvim-cmp
- Replaced `nvim-lsp-installer` with `mason.nvim`
- Added `fidget.nvim` for LSP status updates
- Various README improvements and Windows compatibility fixes
