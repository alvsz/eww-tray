An implementation of the freedesktop [StatusNotifierItem][0] specification (the
successor of appindicators and systray) for [eww][1].

This allows you to use many existing status indicators, e.g. for NetworkManager
or Steam. Menus are supported via jgmenu.

![icons](screenshots/icon.png)
![jgmenu showing a polychromatic menu](screenshots/jgmenu.png)

## Dependencies

-   python3-gi
-   jgmenu

## Configuration

-   In host.py, adapt `render()` to use your icons and colors

Apart from that, feel free to change whatever you like. This repo is meant as
an example, not a turn-key solution.

## Module

```lisp
(deflisten tray "./scripts/host.py")

(defwidget tray []
      (box :orientation "h" :space-evenly true
            (for entry in tray
                  (button :onclick {entry.menu_cmd + " &"}
                          :onrightclick {entry.cmd + " &"}
                          (image :image-height 20
                                 :path {entry.IconPath})))))
```

[0]: https://www.freedesktop.org/wiki/Specifications/StatusNotifierItem/
[1]: https://github.com/elkowar/eww
