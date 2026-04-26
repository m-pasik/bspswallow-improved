# bspswallow (improved)
Adds functionality provided by the dwm "swallow" patch to bspwm.

Modified to allow hiding and showing windows on demand.

# Dependencies

* bspwm (obviously)
* xprop
* dmenu

# Installation
Add two files to ~/.config/bspwm

* noswallow - list of classes of windows that you don't want to swallow the terminal

* terminals - list of classes of terminals that you want to be swallowed

If a class isn't available (such as with xev) then the command of origin can be used.

(example files are included in "examples")

Place bspswallow into your PATH and add the following line to your bspwmrc.

```
pgrep bspswallow || bspswallow &
```

Now just restart bspwm and you're good to go.

You can hide/show the current window by running `bspswallow hide/show`, you can also provide the node ID as the second argument.

If you want to display the list of hidden windows in dmenu run `bspswallow select`.

If you want to use a dmenu replacement, such as rofi set the environment variable `$DMENU` before running `bspswallow select`, for example:

```
export DMENU="rofi -dmenu"
```

# Known Issues

* Incompatability with LibreOffice due to it having a splash screen and spawning multiple windows, use --no-logo when launching and turn off "Tip of the day" in order to avoid this issue.
* ~~Due to the way the script works, programs opened with dmenu_run will still swallow the teminal. This issue can be avoided by using the script noswallow_dmenu in examples/scripts instead of dmenu_run.~~ this is now only an issue with windows without the \_NET\_WM\_PID xproperty (for example sxiv)
