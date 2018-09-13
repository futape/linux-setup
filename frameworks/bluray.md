# Blu-ray & HD-DVD Playback

+   <https://wiki.ubuntuusers.de/Blu-Ray_wiedergeben>
+   <https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD>
+   <http://www.videolan.org/developers/libbluray.html>



## Installation

+   `libbluray2`
+   `libbluray-bdj`

<!---->

    sudo apt-get install libbluray2 libbluray-bdj



### libaacs & libbdplus

+   <http://askubuntu.com/a/219174>
+   <http://vlc-bluray.whoknowsmy.name/>
+   <http://www.labdv.com/aacs/>
+   <http://www.videolan.org/developers/libaacs.html>
+   <http://www.videolan.org/developers/libbdplus.html>

Falls anstelle der Emulation von libaacs und libbdplus durch die [libmmbd](http://www.makemkv.com/forum2/viewtopic.php?f=10&t=7008) Library, welche von MakeMKV zur Verfügung gestellt wird, die Open-Source Varianten verwendet werden sollen, müssen folgende Pakete installiert werden. `libbdplus0` ist erst ab Ubuntu 15.10 in den [offiziellen Paketquellen](https://launchpad.net/ubuntu/+source/libbdplus) enthalten.

+   `libaacs0`
+   `libbdplus0`

<!---->

    sudo apt-get install libaacs0 libbdplus0

Da so nicht mehr die in MakeMKV integrierten AACS Keys verwendet werden, müssen diese manuell zur Verfügung gestellt werden.

    mkdir -p ~/.config/aacs
    cd ~/.config/aacs
    wget http://www.labdv.com/aacs/KEYDB.cfg

Alternativ können die Keys auch aus einer der folgenden Quellen bezogen werden:

+   [Blu-ray VUKs auf Doom9.org](http://forum.doom9.org/showthread.php?t=120988)
+   [HD-DVD VUKs auf Doom9.org](http://forum.doom9.org/showthread.php?t=120611)
+   <http://vlc-bluray.whoknowsmy.name/>
