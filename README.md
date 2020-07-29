# ds-gnome

## Description

Styling guide and resources based on the representation of Kali Linux in Ubisoft's Watch Dogs 2.

Reference article: [https://www.behance.net/gallery/45126777/Watch-Dogs-2-Graphic-Direction](https://www.behance.net/gallery/45126777/Watch-Dogs-2-Graphic-Direction)

![https://mir-s3-cdn-cf.behance.net/project_modules/1400_opt_1/1db75345126777.582a6be3943ba.jpg](https://mir-s3-cdn-cf.behance.net/project_modules/1400_opt_1/1db75345126777.582a6be3943ba.jpg)

Software depicted: Armitage, [Empire](https://github.com/EmpireProject/Empire), GNOME, Terminator

## Usage

Log out select GNOME Classic as your session, then log back in again.

## Guide

### Fonts

These are up to personal preference really, as the ones listed in the reference article are non-free, but if you are on Ubuntu or a derivative, Ubuntu Regular looks pretty good for the interface.

```
gsettings set org.gnome.desktop.interface font-name 'Ubuntu 11'
gsettings set org.gnome.desktop.interface document-font-name 'Ubuntu 11'
gsettings set org.gnome.desktop.wm.preferences titlebar-font 'Ubuntu 11'
```

For the monospace font, [https://sourcefoundry.org/hack/](https://sourcefoundry.org/hack/) works well.

### Panel

Make the following changes in /usr/share/gnome-shell/extensions/apps-menu@gnome-shell-extensions.

```
let index = Main.sessionMode.panel.left.indexOf('activities') + 1;
Main.panel.addToStatusArea('apps-menu', appsMenuButton, index, 'left');
```
```
let index = Main.sessionMode.panel.left.indexOf('activities') + 1;
// Main.panel.addToStatusArea('apps-menu', appsMenuButton, index, 'left');
Main.panel.addToStatusArea('apps-menu', appsMenuButton, 20, 'right');
```

Make the following changes in /usr/share/gnome-shell/extensions/places-menu@gnome-shell-extensions.gcampax.github.com/extension.js.

```
let pos = Main.sessionMode.panel.left.indexOf('appMenu');
    if ('apps-menu' in Main.panel.statusArea)
	pos++;
Main.panel.addToStatusArea('places-menu', _indicator, pos, 'left');
```
```
let pos = Main.sessionMode.panel.left.indexOf('appMenu');
    if ('apps-menu' in Main.panel.statusArea)
	pos++;
// Main.panel.addToStatusArea('places-menu', _indicator, pos, 'left');
Main.panel.addToStatusArea('places-menu', _indicator, 20, 'right');
```

Install Activities Configurator extension from [https://extensions.gnome.org/extension/358/activities-configurator/](https://extensions.gnome.org/extension/358/activities-configurator/)

- Set icon to profile picture (can be found at /var/lib/AccountsService/icons/USERNAME)
- Set icon scale to "1.9"
- Set icon padding to "0"
- Set text to "User: USERNAME@HOSTNAME"
- Disable hotcorner
- Hide panel rounded corners

### Session

This is just a modified version of the GNOME Classic session.

```
sudo cp /usr/share/gnome-shell/modes/classic.json /usr/share/gnome-shell/modes/classic-default.json
sudo cp shell/classic.json /usr/share/gnome-shell/modes
```

### Terminal

Terminal colours are based on the Isotope theme found [here](http://terminal.sexy).

```
sudo apt install -y terminator
cp configs/terminator ~/.config/terminator/config
```

### Theme

Adwaita is the default on GNOME and looks close enough to the concept, however if you want a slightly more accurate look, you can try the [Deepin GTK theme](), though I chose Adwaita because the shell theme that ships with Deepin is unfinished/broken as of writing this and the GTK theme looks slightly out of place when used with the classic panel.

The shell theme here is just a slightly modified version of the one found in the GNOME Classic session which should be included in the `gnome-session` Debian package. The default CSS file can be found at /usr/share/gnome-shell/theme/gnome-classic.css.

```
mkdir -p .themes/DedSec/gnome-shell
cp shell/gnome-shell.css ~/.themes/DedSec/gnome-shell
```

Set GTK theme to Adwaita and shell theme to Classic.

For the cursor theme, you can use this [https://www.gnome-look.org/p/1230923/](https://www.gnome-look.org/p/1230923/) for a more retro look, although Adwaita works fine too.

### Wallpaper

Modified from the [DedSec Fankit](https://news.ubisoft.com/en-us/article/13qrfvKY8TBLMHHDSe2zdh/watch-dogs-2-grab-the-dedsec-fankit-and-marcus-holloway-cosplay-guide).

```
cp wallpaper.jpg ~/Pictures
gsettings set org.gnome.desktop.background picture-uri file://$HOME/Pictures/wallpaper.jpg
```
