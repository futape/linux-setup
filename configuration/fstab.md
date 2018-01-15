# `/etc/fstab`

1.      sudo mkdir /media/daten /media/projekte /media/ext-tuxedo-backup /media/ext-medien /media/ext-medien-2 /media/ext-medien-3 /media/ext-medien-4 /mnt/win-projekte
        sudo chown $USER:$(id -g) /media/daten /media/projekte /media/ext-tuxedo-backup /media/ext-medien /media/ext-medien-2 /media/ext-medien-3 /media/ext-medien-4 /mnt/win-projekte
        sudo mkdir /mnt/windows /mnt/windows-sys /mnt/plex-tmp
        sudo chown plex:plex /mnt/plex-tmp
2.  `sudo blkid`
3.  `sudo nano /etc/fstab`
4.  Die Root- und Swap-Partitionen sollten bei der Installation bereits eingerichtet worden sein.
    Alle anderen mit den Informationen des `blkid` Befehls ergänzen. Die UUIDs müssen ggf. angepasst werden.

        # "Windows" partition unter /mnt/windows mounten
        UUID=92120E63120E4CA3  /mnt/windows  ntfs  defaults,ro,noexec,nosuid,nodev  0  0

        # "(Windows) System-reserviert" partition unter /mnt/windows-sys mounten
        UUID=6CC2FDB3C2FD819E  /mnt/windows-sys  ntfs  defaults,ro,noexec,nosuid,nodev  0  0

        # "Daten" partition unter /media/daten mounten (user-mapping aktiviert)
        UUID=26EC6FC4EC6F8CBD  /media/daten  ntfs  defaults,hide_hid_files,windows_names,inherit,compression  0  0

        # "Projekte" partition unter /media/projekte mounten
        UUID=d4d1b131-aedc-47ed-8acc-d2d28033a174  /media/projekte  ext4  defaults  0  2

        # "Projekte (Windows)" partition unter /mnt/win-projekte mounten (user-mapping aktiviert)
        UUID=0245A7DC622EBD9F  /mnt/win-projekte  ntfs  defaults,hide_hid_files,windows_names,inherit,compression  0  0

        # "Plex (temp)" partition unter /mnt/plex-tmp mounten
        UUID=8f85d49d-1e8f-4ef7-8157-08af5c474435  /mnt/plex-tmp  ext4  defaults  0  2

        # externe "TUXEDO Backup" partition unter /media/ext-tuxedo-backup mounten
        UUID=b85f08b1-4ead-4ef4-b00d-2527dd66cd51  /media/ext-tuxedo-backup  ext4  defaults,noauto,user  0  0

        # externe "Medien" partition unter /media/ext-medien mounten
        UUID=5CB148DB1188CDFB  /media/ext-medien  ntfs  defaults,noauto,user,hide_hid_files,uid=1000,gid=1000,fmask=7111,dmask=7000  0  0

        # externe "Medien 2" partition unter /media/ext-medien-2 mounten
        UUID=7D4B9F7D0B6518B9  /media/ext-medien-2  ntfs  defaults,noauto,user,hide_hid_files,uid=1000,gid=1000,fmask=7111,dmask=7000  0  0

        # externe "Medien 3" partition unter /media/ext-medien-3 mounten
        UUID=167E07325AE39AAC  /media/ext-medien-3  ntfs  defaults,noauto,user,hide_hid_files,uid=1000,gid=1000,fmask=7111,dmask=7000  0  0

        # externe "Medien 4" partition unter /media/ext-medien-4 mounten
        UUID=3627576D017384E3  /media/ext-medien-4  ntfs  defaults,noauto,user,hide_hid_files,uid=1000,gid=1000,fmask=7111,dmask=7000  0  0
5. Zuletzt muss für NTFS-3G noch die SUID-Bit gesetzt werden, damit NTFS-Laufwerke auch ohne Adminrechte eingebunden werden können:

        sudo chmod +s /bin/ntfs-3g
