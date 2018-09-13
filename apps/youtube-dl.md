# youtube-dl

+   <http://youtube-dl.org/>
+   <https://wiki.ubuntuusers.de/youtube-dl/>



## Installation

+   <https://wiki.ubuntuusers.de/youtube-dl/#Manuell>
+   <http://rg3.github.io/youtube-dl/download.html>

<!---->

+   youtube-dl
+   `ffmpeg`
+   `rtmpdump`

<!---->

1.	Zuerste ein eventuell installiertes `youtube-dl` Paket deinstallieren:

		sudo apt-get remove youtube-dl

2.	Anschließend weitere benötigte Pakete installieren:

    	sudo apt-get install ffmpeg rtmpdump

    (Benötigt außerdem Python in Version 2.6, 2.7, 3.2 oder neuer)
3.	Zuletzte die youtube-dl Binary herunterladen und ausführbar machen:

		sudo curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl
	    sudo chmod a+rx /usr/local/bin/youtube-dl

Die Aktualisierung von youtube-dl erfolgt in diesem Fall nicht (wie im ersten Fall) über die Paketverwaltung, sondern mittels des Aufrufs von `sudo youtube-dl -U`.



## Einrichtung

1.	In der Datei `/etc/youtube-dl.conf` folgende Zeile ergänzen um FFmpeg anstelle von libav zu verwenden und eventuelle Warnungen und Fehler zu vermeiden:

		--prefer-ffmpeg
