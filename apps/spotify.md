# Spotify (Beta)

+   <https://www.spotify.com>
+   <https://www.spotify.com/de/download/linux/>
+   <http://wiki.ubuntuusers.de/Spotify>



## Installation (*stable*)

+   `spotify-client`

```sh
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 931FF8E79F0876134EDDBDCCA87FF9DF48BF1C90
echo deb http://repository.spotify.com stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list
sudo apt-get update
sudo apt-get install spotify-client
```



## Hinweise

+   Falls Spotify nach dem Starten nicht in der Window List (*Taskbar*) angezeigt wird, kann einer der folgenden Workarounds helfen (sortiert nach Vorzügen):

    +   <https://github.com/linuxmint/Cinnamon/issues/4858#issuecomment-186565789>
    +   <https://github.com/linuxmint/Cinnamon/issues/4858#issuecomment-162721854>
    +   <https://community.spotify.com/t5/Desktop-Linux-Windows-Web-Player/Linux-Spotify-not-showing-in-window-list/m-p/1288097/highlight/true#M149787>
