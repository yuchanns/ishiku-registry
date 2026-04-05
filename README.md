# ishiku-registry

Registry data for `ishiku.nvim`.

`ishiku-registry` provides two kinds of data:

- parser metadata used by `ishiku.nvim` to install and update parsers
- runtime query files used by `vim.treesitter`

This repository is entirely AI-generated.

## Contents

- `registry/parsers.lua`
  parser sources and install metadata
- `lockfile.json`
  pinned parser revisions, including Neovim-version-aware entries such as `nvim-0.11` and `nvim-0.12`
- `queries/<lang>/*.scm`
  runtime queries activated by `ishiku.nvim`

## Query Coverage

The registry can ship Treesitter runtime queries for external languages, including:

- `highlights.scm`
- `folds.scm`
- `indents.scm`
- `injections.scm`
- `locals.scm`
- `textobjects.scm`

`textobjects.scm` files are used by the `ishiku.nvim` textobjects module to provide:

- select
- move
- swap
- repeatable_move
- incremental_selection
- lsp_interop

## Relationship With ishiku.nvim

- `ishiku.nvim` installs parsers and activates this registry on `runtimepath`
- `ishiku-registry` supplies parser definitions and runtime query data
- `vim.treesitter` consumes the active parser plus the queries from this registry

## Versioning

Parser revisions may need to track the Neovim runtime shipped by a specific Neovim release.
For bundled languages such as `lua`, `vim`, `query`, `markdown`, and `vimdoc`, the
registry lockfile can pin revisions by Neovim version to keep parser nodes compatible
with runtime queries.

## Textobjects

This registry vendors `textobjects.scm` query files derived from the upstream
`nvim-treesitter-textobjects` query set so that `ishiku.nvim` can provide
textobject behavior without depending on the archived runtime plugin.
