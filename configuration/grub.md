# GRUB 2

+   <https://wiki.ubuntuusers.de/GRUB_2/>
+   <https://wiki.ubuntuusers.de/GRUB_2/Konfiguration/>
+   <https://wiki.ubuntuusers.de/GRUB_2/Aussehen/#Aufloesung>
+   <https://wiki.ubuntuusers.de/GRUB_2/Terminalbefehle>

<!---->

1.  Den Computer neustarten und im GRUB Menü mittels `C` in die GRUB Shell wechseln. Dort durch den Aufruf von `videoinfo` die verfügbaren Auflösungen auslesen und durch einen Druck auf `Esc` wieder ins Menü zurückkehren und Linux starten.
2.  Die Datei `/etc/default/grub` in einem Editor mit Schreibrechten öffnen und folgendes ergänzen.
3.  Den Standard-Boot-Eintrag (vorzugsweise die primäre Linux Installation) mittels `GRUB_DEFAULT` festlegen (bspw. `GRUB_DEFAULT=0` für den ersten Eintrag).
4.  Die automatische Auswahl des zuletzt ausgewählten Eintrags durch das Hinzufügen von `GRUB_SAVEDEFAULT=false` bzw. durch das Auskommentieren von `GRUB_SAVEDEFAULT=true` deaktivieren.
5.  Das Verstecken des Menüs durch Auskommentieren von `GRUB_HIDDEN_TIMEOUT` deaktivieren. Außerdem kann `GRUB_HIDDEN_TIMEOUT_QUIET` auskommentiert werden.
6.  `GRUB_DISABLE_OS_PROBER` auf `false` setzen bzw. die Zeile auskommentieren.
7.  Das Menü-Timeout mittels `GRUB_TIMEOUT=4` aus 4 Sekunden setzen.
8.  Das Hinzufügen von `GRUB_TIMEOUT_STYLE=menu` bzw. das Auskommentieren der Option fürt dazu, dass das Menü *immer* angezeigt wird. Alternativ kann `GRUB_TIMEOUT_STYLE` auch auf `countdown` gesetzt werden, was dazu führt, dass das Anzeigen des Menüs deaktiviert wird falls nur ein Betriebssystem zur Auswahl steht und stattdessen einen Countdown von der mittels `GRUB_TIMEOUT` angegebenen Zeit eingeblendet wird.
9.  Die Zeile `GRUB_RECORDFAIL_TIMEOUT` auskommentieren.
10. Falls eine Windows Recovery Partition besteht, sollte diese mittels `GRUB_OS_PROBER_SKIP_LIST="<UUID>@<Partition>"` (z.B. `BAEE3575EE352B51@/dev/sda2`) aus dem Boot-Menü ausgeschlossen werden. Anderenfalls kann diese Zeile auskommentiert werden.
11. Optional kann mittels `GRUB_DISABLE_SUBMENU=y` die hierarchische Menüstruktur deaktiviert werden, sodass stattdessen alle Menüeintrage (inkl. `Recovery` und `Init`-Mode) auf der ersten Menüebene angezeigt werden.
12. Falls kein besonderes Theme gewünscht ist, sollte die Zeile `GRUB_THEME` auskommentiert werden, sodass das Standrad-Debian-Theme verwendet wird.
13. Die `GRUB_TERMINAL` Zeile sollte auskommentiert werden.
14. Grundsätzlich versucht GRUB automatisch die höchste verfügbare Auflösung einzustellen, allerdings gelingt dies bei einem Multi-Sscreen-Setup nicht immer perfekt, sodass die Auflösung manuell gewählt werden muss. Dies geschieht indem man die Option `GRUB_GFXMODE` auf den höchsten der unter *1.* ermittelten Werte setzt und `GRUB_GFXPAYLOAD_LINUX=keep` ergänzt. Optional kann auch noch `GRUB_VIDEO_BACKEND=vbe` hinzugefügt werden um VBE als GRUB Video-Treiber zu erzwingen.
15. Die Option `GRUB_DISABLE_RECOVERY` sollte auskommentiert bzw. auf `false` gesetzt werden.
16. `GRUB_INIT_TUNE` sollte ebenfalls auskommentiert werden, sodass nach dem Laden des GRUB Menüs kein Piep-Ton ausgegeben wird.
17. Alle weiteren Optionen können bei Bedarf auskommentiert bzw. deaktiviert werden.
18. Zuletzt entfernt man durch den Befehl `sudo chmod -x /etc/grub.d/20_memtest86+` die `memtest86+` Menüeinträge.
19. `sudo update-grub` ausführen um die Konfiguration in die `/boot/grub/grub.cfg` Datei zu schreiben.

Eine Übersicht aller verfügbaren Konfigurations-Optionen erhält man mittels `info -f grub -n 'Simple configuration'`.
