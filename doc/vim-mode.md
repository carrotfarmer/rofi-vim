# Vim mode

rofi-vim displays standard Rofi behavior until Vim mode is enabled. 

## Enabling Vim mode

Launch Rofi with:

```sh
rofi \
  -vim-mode true \
  -kb-vim-normal-mode Escape \
  -kb-cancel "Control+g,Control+bracketleft" \
  -show drun
```

**The separate cancel binding is important because Rofi normally maps `Escape`
to `kb-cancel`.**

To run it normally, add this to `~/.config/rofi/config.rasi`:

```rasi
configuration {
    vim-mode: true;
    kb-vim-normal-mode: "Escape";
    kb-cancel: "Control+g,Control+bracketleft";
}
```

You can then use:

```sh
~/.local/bin/rofi -show drun
```


## Keybindings

These standard Vim keybindings are currently supported:

| Key | Action |
| --- | --- |
| `esc` | Enter Normal mode / cancel a pending operation / exit from Normal mode |
| `i`, `a`, `I`, `A` | Insert mode / jump to next char + insert / start of line + insert / end of line + insert |
| `h`, `l` | Move by chars (in the rofi input menu) |
| `w`, `b` | Move by word |
| `0`, `$` | Move to the beginning or end |
| `x`, `X` | Delete the next or previous character |
| `dw`, `db`, `d0`, `d$`, `dd` | Delete using a motion |
| `D` | Delete to the end |
| `C` | Delete to the end and enter Insert mode |
| `r{character}` | Replace the character under the cursor |
| `j`, `k` | Select the next or previous search result |
| `q` | Exit from Normal mode |
| `Enter` | Open the selected result |
| `Ctrl+G`, `Ctrl+[` | Exit from any mode |

## Mode indicators

Add these rules at the bottom of `~/.config/rofi/config.rasi`, outside the
`configuration {}` block. If you use a separate theme file, add them there
instead.

```rasi
case-indicator vim-insert {
    text-color: var(active-foreground);
}

case-indicator vim-normal {
    text-color: var(normal-foreground);
}

case-indicator vim-delete,
case-indicator vim-replace {
    text-color: var(urgent-foreground);
}
```

Normal mode switches to an underline cursor by default. Its dimensions can also be modified:

```rasi
entry {
    underline-cursor-height: 2px;
    underline-cursor-width: 8px;
}
```
