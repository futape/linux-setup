# Spotify (Beta)

+   <https://www.spotify.com>
+   <https://www.spotify.com/de/download/linux/>
+   <http://wiki.ubuntuusers.de/Spotify>



## Installation (*stable*)

+   `spotify-client`

<!---->

    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886
    echo deb http://repository.spotify.com stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list
    sudo apt-get update
    sudo apt-get install spotify-client



### Alternative (*testing*)

+   `spotify-client`

<!---->

    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886
    echo deb http://repository.spotify.com testing non-free | sudo tee /etc/apt/sources.list.d/spotify.list
    sudo apt-get update
    sudo apt-get install spotify-client



## Hinweise

+   Früher existierte nur das Paket `spotify-client-qt` mit einem Qt-basierten GUI. Um den Spotify Client dennoch auch unter GNOME zu benutzten gab es außerdem das Paket `spotify-client-gnome-support`, welches, parallel neben `spotify-client-qt` installiert, Unterstützung für GNOME hinzufügte.
    Heute ist das zu installiertende Paket `spotify-client`, welches die beiden oben ganannten Pakete kombiniert. <!--?--> `spotify-client-qt` und `spotify-client-gnome-support` sind quasi nur noch Platzhalter (*Virtual packages*) für `spotify-client`.
+   Falls Spotify nach dem Starten nicht in der Window List (*Taskbar*) angezeigt wird, kann einer der folgenden Workarounds helfen (sortiert nach Vorzügen):

    +   <https://github.com/linuxmint/Cinnamon/issues/4858#issuecomment-186565789>
    +   <https://github.com/linuxmint/Cinnamon/issues/4858#issuecomment-162721854>
    +   <https://community.spotify.com/t5/Desktop-Linux-Windows-Web-Player/Linux-Spotify-not-showing-in-window-list/m-p/1288097/highlight/true#M149787>
