# adbFire

+   <http://www.jocala.com/adbfire.html>



## Installation

+   adbFire

<!---->

1.  Die aktuelle Version von <http://www.jocala.com/adbfire.html> herunterladen.
2.  ZIP-Archiv entpacken und entpackten Ordner als `adbfire` nach `/opt` verschieben.
3.  Symlink für `/opt/adbfire/adbFire` als `/usr/bin/adbfire` anlegen.

        sudo ln -s /opt/adbfire/adbFire /usr/bin/adbfire
4.  `adbfire.desktop` Datei unter `/usr/share/applications` anlegen und mit folgendem Inhalt füllen (Leerzeile am Ende nicht vergessen):

        [Desktop Entry]
        Name=adbFire
        Comment=Companion program for XBMC and Amazon Fire TV
        Categories=Utility
        GenericName=Hacking Tool
        Icon=adbfire

        Exec=adbfire
        Terminal=false
        Type=Application
5.  Das `adbfire.png` Icon nach `/usr/share/pixmaps` kopieren.
