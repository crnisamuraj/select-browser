# select-browser

all credits goes to anthony perron: https://unix.stackexchange.com/users/407313/anthony-perron

Answer on stack exchange:
https://unix.stackexchange.com/questions/487203/choose-which-browser-to-open-link-in



A simple solution with zenity

create `/usr/bin/select-browser`

```
#!/bin/sh

BROWSER=$(zenity --list --radiolist --text '' --column='check' --column=browser --title='select your browser' TRUE "chromium" FALSE "firefox" FALSE "google-chrome-stable")
$BROWSER $* &

```
To configure OS (Manjaro for me):

create `.local/share/applications/select-browser.desktop`
```
[Desktop Entry]
Version=1.1
Type=Application
Name=Select browser
GenericName=Navigateur Web
Comment=Accéder à Internet
Icon=google-chrome
Exec=/usr/bin/select-browser %U
Actions=new-window;new-private-window;NewShortcut;NewShortcut1;
MimeType=text/html;text/xml;application/xhtml_xml;image/webp;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
Categories=Network;WebBrowser;
StartupNotify=true
StartupWMClass=select-browser

```


modify `.local/share/applications/defaults.list`
run `xdg-settings set default-web-browser select-browser.desktop`
