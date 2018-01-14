# MakeMKV

+   <http://wiki.ubuntuusers.de/MakeMKV>



## Installation

+   `makemkv-bin`
+   `makemkv-oss`

<!---->

    sudo add-apt-repository ppa:heyarje/makemkv-beta
    sudo apt-get update
    sudo apt-get install makemkv-bin makemkv-oss



### Alternative

+   `makemkv-bin`
+   `makemkv-oss`

Befolge die Anweisungen unter <http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224>.



## Einrichtung

1.  Den Beta Lizenzschlüssel von <http://www.makemkv.com/forum2/viewtopic.php?f=5&t=1053> kopieren.
2.  MakeMKV öffnen.
3.  Unter ***Hilfe* &gt; *Registrieren*** den Key einfügen und bestätigen.
4.  MakeMKV beenden.



### libaacs & libbdplus Emulation

+   <https://wiki.ubuntuusers.de/MakeMKV#Direktes-Abspielen-im-Mediaplayer>
+   <http://www.makemkv.com/forum2/viewtopic.php?f=3&t=7009>

<!---->

1.  Die Open-Source Varianten von libaacs und libbdplus deinstallieren. libbdplus ist erst ab Ubuntu 15.10 in den [offiziellen Paketquellen](<https://launchpad.net/ubuntu/+source/libbdplus>) enthalten.

        sudo apt-get remove libaacs0 libbdplus0
2.  [libmmbd](http://www.makemkv.com/forum2/viewtopic.php?f=10&t=7008) als Ersatz einrichten.

        sudo ln -s /usr/lib/libmmbd.so.0 /usr/lib/libaacs.so.0
        sudo ln -s /usr/lib/libmmbd.so.0 /usr/lib/libbdplus.so.0
