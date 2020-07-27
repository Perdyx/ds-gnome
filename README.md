# wd2-gnome

## Description

Styling guide and resources based on the representation of Kali Linux in Ubisoft's Watch Dogs 2.

Reference article: [https://www.behance.net/gallery/45126777/Watch-Dogs-2-Graphic-Direction](https://www.behance.net/gallery/45126777/Watch-Dogs-2-Graphic-Direction)

![https://mir-s3-cdn-cf.behance.net/project_modules/1400_opt_1/1db75345126777.582a6be3943ba.jpg](https://mir-s3-cdn-cf.behance.net/project_modules/1400_opt_1/1db75345126777.582a6be3943ba.jpg)

Software depicted: Armitage, [Empire](https://github.com/EmpireProject/Empire), GNOME, Terminator

## Guide

### Wallpaper

Pulled from the [DedSec Fankit](https://news.ubisoft.com/en-us/article/13qrfvKY8TBLMHHDSe2zdh/watch-dogs-2-grab-the-dedsec-fankit-and-marcus-holloway-cosplay-guide).

```
cp wallpaper.jpg ~/Pictures
gsettings set org.gnome.desktop.background picture-uri file://$HOME/Pictures/wallpaper.jpg
```

### Fonts

These are up to personal preference really, but if you are on Ubuntu or a derivative, Ubuntu Regular looks pretty good.

```
gsettings set org.gnome.desktop.interface font-name 'Ubuntu 11'
gsettings set org.gnome.desktop.interface document-font-name 'Ubuntu 11'
gsettings set org.gnome.desktop.wm.preferences titlebar-font 'Ubuntu 11'
```

### Theme

Adwaita is the default on GNOME and looks close enough to the concept, however if you want a slightly more accurate look, you can try the [Deepin GTK theme](), though I chose Adwaita because the shell theme that ships with Deepin is unfinished/broken as of writing this and the GTK theme looks slightly out of place when used with the classic panel.

The shell theme here is just a slightly modified version of the one found in the GNOME Classic session which should be included in the `gnome-session` Debian package. The default CSS file can be found at /usr/share/gnome-shell/theme/gnome-classic.css.

`cp themes/Classic ~/.themes/Classic`

Set GTK theme to Adwaita and shell theme to Classic.

### Terminator

Terminal colours are based on the Isotope theme found [here](http://terminal.sexy).

```
sudo apt install -y terminator
cp terminator/config ~/.config/terminator/config
```

### Panel

Change `Main.panel.addToStatusArea('apps-menu', appsMenuButton, index, 'left');` to `Main.panel.addToStatusArea('apps-menu', appsMenuButton, 20, 'right');` in /usr/share/gnome-shell/extensions/apps-menu@gnome-shell-extensions.gcampax.github.com/extension.js.

Change `Main.panel.addToStatusArea('places-menu', _indicator, pos, 'left');` to `Main.panel.addToStatusArea('places-menu', _indicator, 20, 'right');` in /usr/share/gnome-shell/extensions/places-menu@gnome-shell-extensions.gcampax.github.com/extension.js.

Install Activities Configurator extension from [https://extensions.gnome.org/extension/358/activities-configurator/](https://extensions.gnome.org/extension/358/activities-configurator/)

- Set icon to profile picture (can be found at /var/lib/AccountsService/icons/USERNAME)
- Set icon scale to "1.9"
- Set icon padding to "0"
- Set text to "User: USERNAME@HOSTNAME"
- Disable hotcorner
- Hide panel rounded corners
