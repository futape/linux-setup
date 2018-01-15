# Setup à la TUXEDO

+   <http://tuxedo.sh/>
+   <http://webfai.de/>



## TUXEDO Repositories hinzufügen

+   <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=59>

<!---->

1.  `/etc/apt/sources.list.d/tuxedo-computers.list` mit folgendem Inhalt füllen:

        deb http://deb.tuxedocomputers.com/ubuntu xenial main
2.  APT-Pinning in `/etc/apt/preferences.d/tuxedo-computers` anlegen, sodass Pakete aus den Repositories nur installiert werden falls es keine bereits installierte Version des Pakets gibt:

        Package: *
        Pin: release o=TUXEDO Computers
        Pin-Priority: 1
3.  Die Signaturschlüssel für die Paketete aus dem Repository hinzufügen und den Schlüssel überprüfen:

        wget -O - http://deb.tuxedocomputers.com/0x54840598.pub.asc | sudo apt-key add -
        sudo apt-key adv --fingerprint 54840598
        # pub   4096R/54840598 2016-05-12
        # Key fingerprint = E5D0 C320 BBCE 8D21 CDF6  0DD5 120E D28D 5484 0598
        # uid TUXEDO Computers GmbH (www.tuxedocomputers.com) <tux@tuxedocomputers.com>
        # sub 4096R/A5842AD4 2016-05-12
4.  APT Repositories aktualisieren:

        sudo apt-get -o Dpkg::Options::=--force-confdef -o Dpkg::Options::=--force-confnew --fix-missing update



## Funktionstasten für Bildschirmhelligkeit aktivieren

+   <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=113>
+   <https://wiki.ubuntuusers.de/Grafikkarten/Intel/#Kernel-Optionen>

<!---->

1.  In der `/etc/default/grub` Datei Bootoptinen für den Linux Kernel hinzufgen:

        GRUB_CMDLINE_LINUX_DEFAULT="[...] acpi_os_name=Linux acpi_osi= acpi_backlight=vendor"
2.  Die GRUB Konfiguration aktualisieren:

        sudo update-grub



## Fingerprint Scanner

+   <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=65>

<!---->

    sudo apt-get install libfprint0 libpam-fprintd fprint-demo



## Nvidia Grafik

+   <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=385>
+   <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=387>
+   <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=56>

<!---->

+   **Linux Mint 17.X (Ubuntu 14.04)** (falls Skylake CPU): `nvidia-352 mesa-utils`
+   **Linux Mint 18.X (Ubuntu 16.04):** `nvidia-381 mesa-utils nvidia-prime`
+   **Andernfalls:** `nvidia-349 mesa-utils umblebee bumblebee-nvidia primus`

<!---->

    sudo apt-get install <nvidia-packages>

Fall kein Skylake CPU, die Datei `/etc/init/bumblebeed.conf` um folgende Einträge ergänzen (s. <https://github.com/Bumblebee-Project/bbswitch/blob/master/README.md#enable-card-on-shutdown>):

    start on runlevel [2345]
    stop on runlevel [016]

`/etc/default/grub` bearbeiten und nach der Zeile `GRUB_CMDLINE_LINUX_DEFAULT=[...]` folgendes ergänzen (Reihenfolge beachten!):

    GRUB_GFXPAYLOAD_LINUX=1920*1080
    GRUB_CMDLINE_LINUX=nomodeset

Anschließend die GRUB Konfiguration aktualisieren:

    sudo update-grub

Zuletzte DPMS in LightDM deaktivieren (falls installiert):

    wget -O /tmp/dpms-disable http://www.tuxedocomputers.com/support/dpms-disable
    sh /tmp/dpms-disable



## *tuxedo-wmi* Treiber für Flugmodustaste und Tastaturbeleuchtung

**Tastaturbeleuchtung nur für Modelle XC[15|17]0[2|3|4]**

+   <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=26>
+   <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=68>
+	<https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=304>

	sudo apt-get install dkms tuxedo-wmi-dkms

Für die Tastaturbeleuchtung auf den Modellen XC[15|17]0[2|3|4] die Datei `/etc/modprobe.d/tuxedo_wmi.conf` bearbeiten um das Standardprofil festzulegen (s. <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=68>):

    options tuxedo-wmi kb_color=white kb_brightness=10 led_invert



## Stromsparfunktionen des Kernels aktivieren (Userspace Komponenten installieren):

+   <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=428>
+   <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=119>
+   Alternativ TLP: <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=60>

1.  Pakete installieren:

        sudo apt-get install laptop-mode-tools
2.  `/etc/laptop-mode/conf.d/ethernet.conf` bearbeiten um Ethernet Stromsparfunktionen zu deaktivieren:

        CONTROL_ETHERNET=0
3.	In `/etc/laptop-mode/conf.d/runtime-pm.conf` folgendes ergänzen um das deaktivieren von USB-Geräten zu verhindern:

		AUTOSUSPEND_RUNTIME_DEVTYPE_BLACKLIST=usbhid



## Bloatware entfernen

    sudo apt-get remove unity-webapps-common app-install-data-partner



## WLAN Modul Firmware installieren

+   <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=305>
+	<https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=27>
+	<https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=149>

<!---->

1.	Mittels `lspci` das installierte WLAN-Modul auslesen.
1.  Benötigte Firmware auswählen:

    +   `iwlwifi-3160-17.ucode`
    +   `iwlwifi-7260-17.ucode`
    +   `iwlwifi-7265-17.ucode`
    +   `iwlwifi-7265D-21.ucode`
    +   `iwlwifi-8000C-19.ucode`
    +   `iwlwifi-8000C-20.ucode`
    +   `iwlwifi-8000C-21.ucode`
    +   `iwlwifi-8000C-22.ucode`
2.  Ausgewählte Firmware installieren:

        sudo wget -O /lib/firmware/<wlan-firmware> http://www.tuxedocomputers.com/support/iwlwifi/<wlan-firmware>



## Intel i915 Firmware installieren

**Nur für *Skylake* (6th Gen) und *Kaby Lake* (7th Gen) CPUs**

+   <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=319>
+	<https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=317>

<!---->

1.  Benötigte Firmware auswählen:

    +   `kbl_dmc_ver1_01.bin`: `kbl_dmc_ver1.bin`
    +   `skl_dmc_ver1_26.bin`: `skl_dmc_ver1.bin`
    +   `skl_guc_ver6_1.bin`: `skl_guc_ver6.bin`
2.  Ausgewählte Firmware installieren:

        sudo wget -O /lib/firmware/i915/<cpu-firmware> http://www.tuxedocomputers.com/support/i915/<cpu-firmware>
3.  Installierte Firmware verlinken:

        sudo ln -s /lib/firmware/i915/<cpu-firmware> /lib/firmware/i915/<link>



## Initiale Bildschirmhelligkeit nach Neustart

+   <https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=114>

<!---->

1.  Die maximale Helligkeitsstufe ermitteln:

        cat /sys/class/backlight/intel_backlight/max_brightness
2.  In der `/etc/rc.local` Datei die Bildschirmhelligkeit auf einen Anteil der maximale Helligkeitsstufe einstellen (Empfohlen: 80%):

        echo X > /sys/class/backlight/intel_backlight/brightness #X = [0.0 - 1.0] * <max>

(Alternativ kann die Helligkeit mit folgendem Befehl einfach auf 100% gesetzte werden: `cat /sys/class/backlight/intel_backlight/max_brightness > /sys/class/backlight/intel_backlight/brightness`)



## *Werbe*-Scopes in Unity Lenses deaktivieren

    gsettings set com.canonical.Unity.Lenses disabled-scopes "['more_suggestions-amazon.scope', 'more_suggestions-u1ms.scope', 'more_suggestions-populartracks.scope', 'music-musicstore.scope', 'more_suggestions-ebay.scope', 'more_suggestions-ubuntushop.scope', 'more_suggestions-skimlinks.scope']"
    gsettings set com.canonical.Unity.Lenses remote-content-search none



## Airplane Mode LED aktivieren

In der Datei `/etc/rc.local` folgendes ergänzen:

    trigger_src="phy0radio"
    trigger_led="/sys/class/leds/tuxedo::airplane/trigger"
    if which rfkill >/dev/null 2>&1; then
	    if rfkill list | grep -wA2 phy0: | grep -wq "blocked: yes"; then
		    echo 0 >"/sys/class/leds/tuxedo::airplane/brightness"
	    else
		    echo 1 >"/sys/class/leds/tuxedo::airplane/brightness"
	    fi
    fi
    [ -w "$trigger_led" ] && grep -wq "$trigger_src" "$trigger_led" && echo "$trigger_src" >"$trigger_led"



## Weitere Anpassungen

+	[Scroll-Lock Kontrollleuchte](https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=58)
+	[WLAN-Verbindungsstabilität verbessern](https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=62)
+	[XC1505/XC1705: Kopfhörerausgang funktioniert nicht](https://www.linux-onlineshop.de/forum/index.php?page=Thread&threadID=115)
