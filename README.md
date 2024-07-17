## implementing kitty's graphics protocol to zellij

-   the issue: zellij doesn't pass through kitty's graphics escape code, so the image can't be rendered (possibly among other problems)

### kitty graphics protocol escape code

```
<ESC>_G<control data>;<payload><ESC>\
```

### discussion from [an open issue](https://github.com/zellij-org/zellij/issues/2814) about implementing the graphics protocol

from `misaelaguayo`:

```
I've been digging into this a bit more since I would like to see it implemented. It seems that zellij uses alacritty's vte parser to interpret ANSI/VT codes in terminal_pane.rs. Perhaps in the handle_pty_bytes function we can do a similar approach to what was done for fzf and do a no op and not pass in those bytes to the vte_parser
```
