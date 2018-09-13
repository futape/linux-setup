# FFmpeg

+   <https://wiki.ubuntuusers.de/FFmpeg/>



## Installation

+   `ffmpeg`
+   `libavcodec-extra57`
+   `libavdevice57`
+   `libavfilter-extra6`
+   `libavformat57`
+   `libswresample2`
+   `libswscale4`
+   `libpostproc54`

```sh
sudo apt-get install ffmpeg libavcodec-extra57 libavdevice57 libavfilter-extra6 libavformat57 libswresample2 libswscale4 libpostproc54
```



## Fraunhofer FDK AAC

+   <http://wiki.hydrogenaud.io/index.php?title=AAC_encoders#Features>
+   <http://wiki.hydrogenaud.io/index.php?title=Fraunhofer_FDK_AAC>
+   <https://en.wikipedia.org/wiki/Fraunhofer_FDK_AAC>
+   <https://trac.ffmpeg.org/wiki/Encode/AAC>

Der [native FFmpeg AAC En-/Decoder](https://trac.ffmpeg.org/wiki/Encode/AAC#NativeFFmpegAACEncoder) ist nicht die beste verfügbare Option. Die beste Option ist der FDK AAC En-/Decoder des Fraunhofer Instituts, welche u.A. in Android Verwendung findet. Mit `fdk-aac` gibt es einen Port des Projekt als portable Biliothek, welche auch als Debian Package (`libfdk-aac*`) angeboten wird. FFmpeg enthält Support für `libfdk-aac`, allerdings wird FDK AAC nach seiner Lizens als *non-free* betrachtet und ist deshalb nicht in Standard-Builds (Debian, Ubuntu etc.) von FFmpeg enthalten. Um den FDK AAC En-/Decoder trotzdem nutzen zu können muss FFmpeg entweder manuell mit den Optionen `--enable-libfdk-aac` kompiliert werden oder es muss ein *non-free* Build von FFmpeg, welcher Support für `libfdk-aac` aktiviert hat, installiert werden. Einen solchen Build gibt es bspw. für Ubuntu 18.04 *Bionic Beaver* über das `bionic-media` PPA von [Doug McMahon](https://launchpad.net/~mc3man).

```sh
sudo add-apt-repository ppa:mc3man/bionic-media
sudo apt-get update
```

Sollte ein Downgrade von einem zuvor installierten FFmpeg notwendig sein, muss ein APT-Pinning für die PPA Packages mit einer `Pin-Priority` von `1000` eingerichtet werden und die Packages downgegraded werden:

```
Package: ffmpeg* libavcodec* libavdevice* libavfilter* libavformat* libavresample* libavutil* libpostproc* libswresample* libswscale*
Pin: release o=LP-PPA-mc3man-bionic-media
Pin-Priority: 1000
```

Anderenfalls können die *non-free* FFmpeg Packages einfach mittels des unter *Installation* angegebenen Befehls installiert werden.

Weitere Links zum Libav/FFmpeg AAC En-/Decoding:

+   [FFmpeg: Encode / AAC](https://trac.ffmpeg.org/wiki/Encode/AAC)
+   [Libav: Encoding / AAC](https://wiki.libav.org/Encoding/aac)
+   [Libav: avconv Documentation](https://libav.org/avconv.html)
+   [FFmpeg Static Builds von John Van Sickle](https://www.johnvansickle.com/ffmpeg/)
