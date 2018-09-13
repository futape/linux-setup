# KeePass2

+   <http://keepass.info/>
+   <https://sourceforge.net/p/keepass/discussion/329220/thread/17d1bd26/#b262>



## Installation

+   `keepass2`
+   `xdotool`

<!---->

    sudo add-apt-repository ppa:jtaylor/keepass
    sudo apt-get update
    sudo apt-get install keepass2 xdotool



## Einrichtung & Deutsches GUI

1.  Deutsches Sprachpaket für KeePass 2.X+ von <http://keepass.info/translations.html> herunterladen.
2.  ZIP-Archiv entpacken.
3.  `.lngx` Datei nach `$XDG_DATA_HOME/KeePass` (standardmäßig `~/.local/share/KeePass`) bzw. nach `/usr/lib/keepass2` kopieren.
4.  KeePass starten und unter ***View* &gt; *Change Language*** die deutsche Sprache auswählen.
5.  `.kdbx` Datei (KeePass Datenbank) aus der Dropbox in KeePass laden.



## Desktop Environment Integration (Plug-ins)

+   <http://keepass.info/plugins.html#linuxint>
+   <https://github.com/dlech/Keebuntu>
+   <https://launchpad.net/~dlech/+archive/ubuntu/keepass2-plugins>
+   <https://sourceforge.net/p/keepass/bugs/1345/>

<!---->

1.  Das PPA hinzufügen:

        sudo add-apt-repository ppa:dlech/keepass2-plugins
        sudo apt-get update
2.  `keepass2-plugin-application-indicator` oder alternativ `keepass2-plugin-tray-icon` installieren:

        sudo apt-get install keepass2-plugin-application-indicator
