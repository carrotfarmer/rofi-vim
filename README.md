<h1 align="center">rofi-vim</h1>

*rofi-vim* is a fork of [Rofi](https://github.com/davatorium/rofi) that adds modal Vim editing functionality.

See the [Vim mode documentation](doc/vim-mode.md) for configuration and
keybindings. This fork is currently based on Rofi 2.0.0.

<img src="doc/demo.gif">

## Install rofi-vim

Ensure the [build dependencies](INSTALL.md) are installed, then build and install
the `vim-mode` branch under `~/.local`:

```sh
git clone --branch vim-mode --recurse-submodules \
  https://github.com/carrotfarmer/rofi-vim.git

cd rofi-vim
meson setup build --buildtype=release --prefix="$HOME/.local"
meson compile -C build
meson test -C build --print-errorlogs
meson install -C build
```

Run it with:

```sh
~/.local/bin/rofi \
  -vim-mode true \
  -kb-vim-normal-mode Escape \
  -kb-cancel "Control+g,Control+bracketleft" \
  -show drun
```

For safety purposes obviously, these commands do NOT replace the system Rofi installation, which would probably live in `/usr/bin/rofi`. 
Try it out first!

Refer to the
[Vim mode documentation](doc/vim-mode.md) for configuration and the full list of keybindings.
