# Franz

+	<https://wiki.ubuntuusers.de/Franz/>
+	<http://meetfranz.com/>
+	<https://github.com/meetfranz/franz-app/releases>



## Installation

+	Franz

<!---->

1.	`.tgx` Archiv von <http://meetfranz.com/#download_all> herunterladen.
2.	Installationsverzeichnis unter `/opt` erstellen:

		sudo mkdir /opt/franz
3.	Archiv entpacken (Dateinamen anpassen):

		sudo tar -xzf Franz-linux-<arch>-<version>.tgz -C /opt/franz
4.  Symlink für `/opt/franz/Franz` in `/usr/local/bin` erstellen.

        sudo ln -s /opt/franz/Franz /usr/local/bin/franz
5.  Eine `.desktop` Datei erstellen (Die Leerzeile am Ende nicht vergessen). Ein geeignetes Icon befindet sich unter `/opt/franz/resources/app.asar.unpacked/assets/franz.svg`.

        [Desktop Entry]
        Name=Franz
        Comment=A free messaging app for WhatsApp, Facebook Messenger, Telegram, Slack and more.
        Categories=Network
        Icon=/opt/franz/resources/app.asar.unpacked/assets/franz.svg
        Exec=franz
        Terminal=false
        Type=Application



### Alernative

+	`meetfranz`

<!---->

1.	Paketquelle hinzufügen:

		sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2FAB19E7CCB7F415
		echo "deb http://styrion.at/apt/ ./" | sudo tee /etc/apt/sources.list.d/styrion.list
2.	Da es sich bei diesem Repository um ein Sammel-Repository mit vielen verschiedenen Paketen handelt wird in der Datei `/etc/apt/preferences.d/styrion` ein APT-Pinning eingerichtet:

	    Package: *
	    Pin: origin styrion.at
	    Pin-Priority: -1

	    Package: meetfranz
	    Pin: origin styrion.at
	    Pin-Priority: 500
3.	Die Paketquellen aktualisieren:

		sudo apt-get update
4.	Franz installieren:

		sudo apt-get install meetfranz
