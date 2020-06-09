# sloppymove
[Openbox](https://github.com/danakj/openbox)-compatible POSIX shell script to swap two windows' positions or draw a rectangle to move a window into.

![sloppymove](sloppygif.gif)

## Usage

After running sloppymouse via hotkey, you can:

* Click on a window, in which case the currently active window and the targeted window will swap positions.
* Draw a rectangle, in which case the currently active window will move itself inside it.

**Animations are generated at the compositor level. Watch for [this Picom issue](https://github.com/yshui/picom/issues/217) to see the progress on this feature. Current work-in-progress has not yet been made public.**


## Installing

Download sloppymove and make it executable.

```sh
$ git clone https://github.com/alnj/sloppymove.git
$ cd sloppymove
$ chmod +x sloppymove
```

You may now move or symlink sloppymove somewhere inside your `$PATH` so as not to require using its full path when calling it.

```sh
$ mv sloppymove ~/.local/bin/
```

Bind `sloppymove` to a hotkey or mouse button. For example, to bind it to Super+Middle Click, add this to `~/.config/openbox/rc.xml` inside the ` <context name="Frame">...</context>` tag:
```xml
<mousebind button="W-Middle" action="Press">
      <action name="Execute">
            <command>sloppymove</command>
      </action>
</mousebind>
```

Binding sloppymove to a keyboard hotkey is possible using a standalone hotkey daemon such as [sxhkd](https://github.com/baskerville/sxhkd), and even binding it to a mouse shortcut using [this sxhkd patch](https://github.com/periish/patches/tree/master/sxhkd) or [dxhkd](https://github.com/dakyskye/dxhd).


## Dependencies

* xdotool
* xwininfo
* slop      


## Known issues

* Broken/untested on WMs other than Openbox.
* Very inaccurate results with windows with forced aspect ratio such as mpv.
* If using a terminal with hinted geometry, there will be a slight size difference when swapping it with another window (unless swapping it with another terminal).
