# FFmpeg

+   <https://wiki.ubuntuusers.de/FFmpeg/>



## Installation

+   `ffmpeg`
+   `libavcodec-ffmpeg-extra56`
+   `libavdevice-ffmpeg56`
+   `libavfilter-ffmpeg5`
+   `libavformat-ffmpeg56`
+   `libswresample-ffmpeg1`
+   `libswscale-ffmpeg3`
+   `libpostproc-ffmpeg53`

<!---->

    sudo apt-get install ffmpeg libavcodec-ffmpeg-extra56 libavdevice-ffmpeg56 libavfilter-ffmpeg5 libavformat-ffmpeg56 libswresample-ffmpeg1 libswscale-ffmpeg3 libpostproc-ffmpeg53



## Libav Emulation

+   `libav-tools`

<!---->

    sudo apt-get install libav-tools



## Fraunhofer FDK AAC

+   <http://wiki.hydrogenaud.io/index.php?title=AAC_encoders#Features>
+   <http://wiki.hydrogenaud.io/index.php?title=Fraunhofer_FDK_AAC>
+   <https://en.wikipedia.org/wiki/Fraunhofer_FDK_AAC>
+   <https://wiki.libav.org/Encoding/aac>

Der standardmäßig in FFmpeg enthaltene AAC En-/Decoder ist im Vergleich zu anderen verfügbaren Optionen eine ziemlich mangelhafte Lösung. Die beste Option ist der FDK AAC En-/Decoder des Fraunhofer Instituts, welche u.A. in Android Verwendung findet. Mit `fdk-aac` gibt es einen Port des Projekt als portable Biliothek, welche auch als Debian Package (`libfdk-aac*`) angeboten wird. FFmpeg enthält Support für `libfdk-aac`, allerdings wird FDK AAC nach seiner Lizens als *non-free* betrachtet und ist deshalb nicht in Standard-Builds (Debian, Ubuntu etc.) von FFmpeg enthalten. Um den FDK AAC En-/Decoder trotzdem nutzen zu können muss FFmpeg entweder manuell mit den Optionen `--enable-libfdk-aac --enable-nonfree` kompiliert werden oder es muss ein *non-free* Build von FFmpeg, welcher Support für `libfdk-aac` aktiviert hat, installiert werden. Einen solchen Build gibt es bspw. für Ubuntu 16.04 *Xenial Xerus* über das `xerus-media` PPA von [Doug McMahon](https://launchpad.net/~mc3man).

    ffmpeg (7:2.8.11-0ubuntu0.16.04.1+ppa) xenial; urgency=medium

      * add faac, fdkaac, patch mpc

     -- Doug McMahon <email address hidden>  Wed, 15 Feb 2017 08:44:23 -0500

<!---->

    sudo add-apt-repository ppa:mc3man/xerus-media
    sudo apt-get update

Sollte ein Downgrade von einem zuvor installierten FFmpeg notwendig sein, muss ein APT-Pinning für die PPA Packages mit einer `Pin-Priority` von `1001` eingerichtet werden und die Packages mittels `sudo apt-get dist-upgrade` downgegraded werden. Anderenfalls können die *non-free* FFmpeg Packages einfach mittels des unter *Installation* angegebenen Befehls installiert werden.

Weitere Links zum Libav/FFmpeg AAC En-/Decoding:

+   [FFmpeg: Encode / AAC](https://trac.ffmpeg.org/wiki/Encode/AAC) ([Revision 16](https://trac.ffmpeg.org/wiki/Encode/AAC?version=16))
+   [Libav: Encoding / AAC](https://wiki.libav.org/Encoding/aac)
+   [Libav: avconv Documentation](https://libav.org/avconv.html)
+   [FFmpeg Static Builds von John Van Sickle](https://www.johnvansickle.com/ffmpeg/)
