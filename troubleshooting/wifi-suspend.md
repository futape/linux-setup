# WLAN lässt sich nach Erwachen aus dem Sleep Modus (Suspend to RAM) nicht wieder aktivieren

+	<https://ubuntuforums.org/showthread.php?t=2004690&p=12031410#post12031410>
+	<https://wiki.ubuntuusers.de/pm-utils/#Module-vor-SUSPEND-entladen-nach-RESUME-wieder-laden>
+	<https://linux.die.net/man/8/pm-suspend>

<!---->

1.	Den genutzten WLAN Treiber Kernel-Modul auslesen:

		sudo lshw -C network
2.	Das entsprechende Modul während des RESUME Vorgangs neuladen (am Beipiel des Moduls `iwlwifi`):

		echo SUSPEND_MODULES="$SUSPEND_MODULES iwlwifi" | sudo tee /etc/pm/config.d/00sleep_module
		sudo chmod +x /etc/pm/config.d/00sleep_module



## Alternative 1

+	<https://www.reddit.com/r/linuxmint/comments/5dxntl/please_help_linux_mint_18_doesnt_connect_to_wifi/da92rdp/>
+	<https://linux.die.net/man/8/pm-suspend>

<!---->

1.	Den genutzten WLAN Treiber Kernel-Modul auslesen:

		sudo lshw -C network
2.	Das entsprechende Modul während des RESUME Vorgangs neuladen (am Beipiel des Moduls `iwlwifi`). Dazu eine Datei `/etc/pm/sleep.d/00restart_modules` mit folgendem Inhalt erstellen:

		#!/bin/bash
		case "$1" in
			thaw|resume)
				rmmod iwlwifi && modprobe iwlwifi
				;;
		esac
3.	Die Datei ausführbar machen:

		sudo chmod +x /etc/pm/sleep.d/00restart_modules



## Alternative 2

+	<https://askubuntu.com/a/845775>
+	<https://linux.die.net/man/8/pm-suspend>

<!---->

1.	Den Network Manager während des RESUME Vorgangs neustarten. Dazu eine Datei `/etc/pm/sleep.d/00restart_network_manager` mit folgendem Inhalt erstellen:

		#!/bin/bash
		case "$1" in
			thaw|resume)
				service network-manager restart
				;;
		esac
3.	Die Datei ausführbar machen:

		sudo chmod +x /etc/pm/sleep.d/00restart_network_manager
4.	Falls das nicht funktioniert, die folgenden Alternativen in dieser Reihenfolge versuchen:

	1.	Anstelle der `service` Aufrufs `systemctl restart network-manager.service` verwenden.
	2.	Anstelle des `service ... restart` Aufrufs `service network-manager stop && sleep 5 && sudo service network-manager start` verwenden (s. <https://askubuntu.com/a/862734>). Falls das nicht funktioniert, dasselbe nochmal mit dem `systemctl` Befehl versuchen.
	3.	Das Script nach `/lib/systemd/system-sleep` verschieben und `thaw|resume` durch `post` ersetzen (s. <https://askubuntu.com/questions/761180/wifi-doesnt-work-after-suspend-after-16-04-upgrade#comment1305929_845775>). Ebenfalls mit den oben genannten 3 Alternativen testen.



## Alternative 3

+	<https://askubuntu.com/a/761220>

<!---->

1.	Den Network Manager während des RESUME Vorgangs neustarten. Dazu eine Datei `/etc/systemd/system/network-manager-restart.service` mit folgendem Inhalt erstellen:

		[Unit]
		Description=Restart Network Manager at RESUME
		After=suspend.target
		After=hibernate.target
		After=hybrid-sleep.target

		[Service]
		Type=oneshot
		ExecStart=/bin/systemctl restart network-manager.service

		[Install]
		WantedBy=suspend.target
		WantedBy=hibernate.target
		WantedBy=hybrid-sleep.target
3.	Den systemd Service aktivieren:

		sudo systemctl enable network-manager-restart.service
4.	Bei Bedarf stattdessen mit `/bin/systemctl stop network-manager.service && sleep 5 && /bin/systemctl start network-manager.service` testen.



## Weitere Alternativen

+	<https://forums.linuxmint.com/viewtopic.php?p=1135258#p1135258>
+	<https://www.reddit.com/r/linuxmint/comments/5dxntl/please_help_linux_mint_18_doesnt_connect_to_wifi/da87a1w/>
+	<https://askubuntu.com/a/901515>
