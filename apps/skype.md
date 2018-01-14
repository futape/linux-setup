# Skype

+   <https://wiki.ubuntuusers.de/Skype_f%C3%BCr_Linux>
+   <https://www.skype.com>



## Installation

+   `skypeforlinux`

<!---->

1.  Die neueste `.deb` Datei von <https://www.skype.com/de/download-skype/skype-for-computer/> herunterladen.
2.  Installieren.
3.  Bei der Installation wird automatisch die Repository `deb [arch=amd64] https://repo.skype.com/deb stable main` hinzugefügt.
    Zuletzt muss noch der Key hinzugefügt werden:

        sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 1F3045A5DF7587C3
