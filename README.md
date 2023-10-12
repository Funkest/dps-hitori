# dps-hitori


<img src="./image.gif">

Plugin similar to [neovim-remote](https://github.com/mhinz/neovim-remote) and [vim-singleton](https://github.com/thinca/vim-singleton) using [denops.vim](https://github.com/vim-denops/denops.vim).

# Features 

It uses [denops.vim](https://github.com/vim-denops/denops.vim), so it works cross-platform.
Also supports Windows.

# Installation 

If you use [folke/lazy.nvim](https://github.com/folke/lazy.nvim).

```lua
{
  "yukimemi/dps-hitori",
  lazy = false,
  dependencies = {
    "vim-denops/denops.vim",
  },
}
```

If you use [yukimemi/dvpm](https://github.com/yukimemi/dvpm).

```typescript
dvpm.add({ url: "yukimemi/dps-hitori" });
```

# Requirements 

- [Deno - A modern runtime for JavaScript and TypeScript](https://deno.land/)
- [vim-denops/denops.vim: 🐜 An ecosystem of Vim/Neovim which allows developers to write cross-platform plugins in Deno](https://github.com/vim-denops/denops.vim)
# Usage 

No special settings are required.
By default, Start a websocket server on port 7070.

# Commands 

`:Disablehitori`                                              
Disable hitori.

`:Enablehitori`                                                
Enable hitori.

# Config 

No settings are required. However, the following settings can be made if necessary.

`g:hitori_debug`                                              
Enable debug messages.
default is v:false

`g:hitori_opener`                                            
Configure how files are opened.
default is "tab drop"

`g:hitori_quit`                                                
Whether to quit after sending a file to an already open server-side Vim/Neovim.
default is v:true

`g:hitori_ignore_patterns`                          
A list of patterns to be ignored. (JavaScript regexp)
default is ["\\.tmp$", "\\.diff$", "(COMMIT_EDIT|TAG_EDIT|MERGE_|SQUASH_)MSG$"]

`g:hitori_port`                                                
Websocket server port.
default is 7070

# Example 

```vim
let g:hitori_debug = v:false
let g:hitori_quit = v:false
let g:hitori_port = 7070
let g:hitori_opener = "vsplit"
let g:hitori_ignore_patterns = ["\\.tmp$", "\\.diff$", "(COMMIT_EDIT|TAG_EDIT|MERGE_|SQUASH_)MSG$"]
```

# hitori cli command 

Before starting Neovim, you can use the `hitori` command to check if the WebSocket server is already running, and if it is, directly send the path of the argument via the WebSocket, otherwise start Neovim.

To use `nvim`, use the following command:                     

```shell
deno install --force --allow-net --allow-run --allow-read --name hitori https://raw.githubusercontent.com/yukimemi/dps-hitori/main/cmd/hitori_nvim.ts
```

To use `nvim-qt`, use the following command:               

```shell
deno install --force --allow-net --allow-run --allow-read --name hitori https://raw.githubusercontent.com/yukimemi/dps-hitori/main/cmd/hitori_nvim-qt.ts
```

To use `neovide`, use the following command:               

```shell
deno install --force --allow-net --allow-run --allow-read --name hitori https://raw.githubusercontent.com/yukimemi/dps-hitori/main/cmd/hitori_neovide.ts
```

# License 

Licensed under MIT License.

Copyright (c) 2023 yukimemi

