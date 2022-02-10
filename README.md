# What
invim connects to your running Neovim and asks it to open files from a separate process. If you're using Neovim's terminal, it lets you open files from the command line or as [EDITOR](https://bash.cyberciti.biz/guide/$EDITOR_variable) in the Neovim running the terminal.

# Installation
Assuming ~/bin is on your path:

```
curl -o ~/bin/invim -fsSL https://raw.githubusercontent.com/groves/invim/HEAD/invim
chmod 0755 ~/bin/invim
```

If you don't use ~/bin, swap that for another directory on your path.

## To use as your git commit message editor
`git config --global core.editor 'invim --split --remote-wait'`

# Usage

```
  invim [options] file  Edit file in the Neovim running at $NVIM_LISTEN_ADDRESS

Options:
  --remote            Open the file with :edit. This is the default
  -w, --remote-wait   Wait for the file's buffer to be deleted before exiting
  -o, --split         Open the file with :split
  -O, --vsplit        Open the file with :vsplit
  -p, --tabedit       Open the file with :tabedit
  -l, --last          Move to the previous window and open the file with :edit
  -n, --dry-run       Print what Neovim would execute instead of executing it
```

e.g. `invim file_to_open`

# Why
[neovim-remote](https://github.com/mhinz/neovim-remote) does everything invim does and more. invim's sole benefit is that it doesn't require Python and an installed Python package: it's a single Bash script that only relies on Neovim itself.

# What about --remote-send, --remote-expr and other useful commands?
neovim-remote and Vim's remote commands support a bunch of other useful operations. They aren't implemented in invim as I haven't needed them and the implementation is already complicated enough. I don't see anything that would prevent their being added though.
