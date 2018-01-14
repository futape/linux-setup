# PLEX

+   <https://wiki.ubuntuusers.de/Plex_Media_Server/>
+   <https://www.plex.tv>



## Installation

1.  Die neueste `.deb` Datei von <https://www.plex.tv/downloads/> herunterladen.
2.  Installieren.
3.	Bei der Installation wird automatisch das Repository `deb https://downloads.plex.tv/repo/deb/ public main` hinzugefügt. Diese muss allerdings noch in der Datei `/etc/apt/sources.list.d/plexmediaserver.list` einkommentiert werden.
    Zuletzt muss noch der Key hinzugefügt werden:

        wget -q https://downloads.plex.tv/plex-keys/PlexSign.key -O - | sudo apt-key add -
