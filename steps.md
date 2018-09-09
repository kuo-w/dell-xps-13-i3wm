# Configurations

## Brightness

[source](https://askubuntu.com/a/1060843)

1. install xbacklight

```
sudo apt-get install xbacklight
```

2. make link

```
sudo ln -s /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness /sys/class/backlight
```

3. in /etc/X11/xorg.conf:

```
Section "Device"
  Identifier  "Intel Graphics"
  Driver      "intel"
  Option      "Backlight"  "intel_backlight"
EndSection
```

4. logout and login.

Controlling screen brightness from media keys should work as expected.

## Touchpad

[source](https://unix.stackexchange.com/a/440545)

1. in /etc/X11/xorg.conf

```
Section "InputClass"
    Identifier "touchpad"
    Driver "libinput"
    MatchIsTouchpad "on"
    Option "Tapping" "on"
    Option "ScrollMethod" "edge"
EndSection
```

2. logout and login

Touchpad functionality such as tap-to-click and edge-scrolling should be working as expected.

## Polybar (status bar)

[source](https://medium.com/@tatianaensslin/install-polybar-in-3-steps-on-debian-stretch-c64ab6157fb1)

1. install dependencies

```
sudo apt-get install cmake cmake-data libcairo2-dev libxcb1-dev libxcb-ewmh-dev libxcb-icccm4-dev libxcb-image0-dev libxcb-randr0-dev libxcb-util0-dev libxcb-xkb-dev pkg-config python-xcbgen xcb-proto libxcb-xrm-dev i3-wm libasound2-dev libmpdclient-dev libiw-dev libcurl4-openssl-dev libpulse-dev
```

2. clone

```
git clone https://github.com/jaagr/polybar.git
```

3. install Font Awesome. [instructions](https://github.com/jaagr/polybar/wiki/Fonts)

4. build

```
cd polybar && ./build.sh
```

5. set launch configs. [instructions](https://github.com/jaagr/polybar/wiki)

# Optional

## Dotfiles

1. copy over the folders i3 and polybar into ~/.config
2. refresh i3 by:

```
i3-msg reload
i3-msg restart
```

And relaunch Polybar by:

```
$HOME/.config/polybar/launch.sh
```

## Terminal Theme

Use [Gogh](https://github.com/Mayccoll/Gogh) for pre-made themes.

## Caps Lock As Super:

[source](https://faq.i3wm.org/question/490/using-caps-lock-as-mod-key/index.html%3Fanswer=670.html)

1. create file

```
touch ~/.Xmodmap
```

2. append

```
clear Lock
keycode 66 = Hyper_L
add mod4 = Hyper_L
```

3. execute

```
xmodmap ~/.Xmodmap
```

## Wallpaper

1. install feh

```
sudo apt-get install feh
```

2. set wallpaper

```
feh --bg-scale <path_to_image>
```
