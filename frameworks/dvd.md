# DVD Playback

+   <https://wiki.ubuntuusers.de/DVD-Wiedergabe#Libdvdcss>
+   <https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs>
+   <https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs>
+   <http://www.videolan.org/developers/libdvdcss.html>



## Installation

+   `libdvd-pkg`
+   `libudf0`
+   `libdvdcss2`

<!---->

    sudo apt-get install libdvd-pkg libudf0
    sudo dpkg-reconfigure libdvd-pkg

Im Falle einer ruckeligen Wiedergabe kann das Entfernen des `~/.dvdcss` Verzeichnisses helfen.

    rm -r ~/.dvdcss

Außerdem kann es nötig sein dem Laufwerk einen (neuen) [Region Code zuzuweisen](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting_DVD_Region_Codes).
