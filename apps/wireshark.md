# Wireshark (tshark)

+   <https://wiki.ubuntuusers.de/Wireshark/>
+   <https://wiki.ubuntuusers.de/Netzwerk-Monitoring/#Programme-mit-grafischer-Oberflaeche>
+   <https://wiki.ubuntuusers.de/Streams_speichern/#Tshark>



## Installation

+   `wireshark`
+   `tshark`

<!---->

    sudo add-apt-repository ppa:wireshark-dev/stable
    sudo apt-get update
    sudo apt-get install wireshark tshark



## Einrichtung

1.  Das Back-end-Programm `dumpcap` so konfigurieren, dass es der Gruppe `wireshark` angehört und alle Nutzer, die ebenfalls der Grupper angehören den Network-Traffic mitschneiden können und somit keine Root-Rechte mehr erforderlich sind. Dies geschieht über den Befehl `sudo dpkg-reconfigure wireshark-common` und das Bestätigen der Nachfrage ob noch weitere Nutzer außer `root` den Network-Traffic überwachen dürfen.
2.  Anschließend fügt man mit `sudo adduser $USER wireshark ` seinen eigenen Benutzer der Gruppe `wireshark` zu und lädt die Benutzerumgebung neu indem man `newgrp - wireshark` ausführt.
