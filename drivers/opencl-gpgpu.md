# GPGPU Treiber (OpenCL)

+   <https://www.khronos.org/opencl/>
+   <https://de.wikipedia.org/wiki/OpenCL>
+   <http://wiki.tiker.net/OpenCLHowTo#Overview>



## Installation

+   <https://forge.imag.fr/projects/ocl-icd/>

<!---->

+   `ocl-icd-libopencl1`
+   `opencl-headers`

<!---->

    sudo apt-get install ocl-icd-libopencl1 opencl-headers



## Intel CPU

+   [Runtime Downloads](https://software.intel.com/en-us/articles/opencl-drivers)
+   [Runtime Release Notes](https://software.intel.com/en-us/articles/opencl-runtime-release-notes)
+   <https://software.intel.com/en-us/intel-opencl>
+   <https://gist.github.com/rmcgibbo/6314452>
+   <https://software.intel.com/en-us/comment/1808483>
+   <http://mhr3.blogspot.de/2013/06/opencl-on-ubuntu-1304.html>
+   <http://wiki.tiker.net/OpenCLHowTo#Installing_the_Intel_CPU_ICD>

<!---->

+   `opencl-1.2-intel-cpu`
+   `alien`

<!---->

1.  Die aktuelle Runtime von <https://software.intel.com/en-us/articles/opencl-drivers#latest_CPU_runtime> herunterladen.
2.  Heruntergeladenes Archiv entpacken und im Terminal in das entpackte Verzeichnis wechseln.
3.  Notwendige Pakete installieren.

        sudo apt-get install rpm alien
4.  Public Key zu RPM hinzufügen.

        sudo rpm --import PUBLIC_KEY.PUB
5.  Im Terminal in das `rpm` Verzeichnis wechseln.

        cd rpm
6.  Die Signatur des `opencl-1.2-intel-cpu-*.rpm` Pakets verifizieren.

        rpm --checksig opencl-1.2-intel-cpu-*.rpm
7.  Das zuvor verifizierte Paket installieren.

        sudo alien -k -i opencl-1.2-intel-cpu-*.rpm
8.  ICD Datei registrieren.

        sudo mkdir -p /etc/OpenCL/vendors
        sudo ln -s /opt/intel/opencl-1.2-*/etc/intel64.icd /etc/OpenCL/vendors/intel64.icd



### Alternative (*Intel Code Builder*)

+   <https://software.intel.com/en-us/articles/opencl-drivers#latest_linux_SDK_release>
+   <https://software.intel.com/en-us/intel-opencl>
+   **Code Builder Downloads**
    +   <https://software.intel.com/en-us/intel-opencl/download>
    +   <https://software.intel.com/en-us/articles/intel-code-builder-for-opencl-api>
+   **Code Builder Release Notes**
    +   <https://software.intel.com/en-us/articles/opencl-code-builder-release-notes>
    +   <https://software.intel.com/en-us/articles/standalone-code-builder-release-notes> (mit Installationsanweisungen)
+   [Code Builder User Manual](https://software.intel.com/en-us/code-builder-user-manual)
+   <http://askubuntu.com/questions/545763/installation-of-intel-opencl#question>

<!---->

1.  Die aktuelle Version des *Code Builders für Ubuntu* [hier](https://software.intel.com/en-us/articles/intel-code-builder-for-opencl-api) herunterladen und das heruntergeladene Archiv entpacken.
2.  Mit dem Terminal in das entpackte Verzeichnis wechseln.
3.  `rpm` installieren.

        sudo apt-get install rpm
4.  Public Key zu RPM hinzufügen.

        sudo rpm --import PUBLIC_KEY.PUB
5.  Die Signatur der `.rpm` Pakete verifizieren.

        rpm --checksig rpm/*.rpm
6.  Code Builder und Runtime installieren.

        sudo ./install.sh
7.  Den Intel ICD Loader durch die Referenzimplementierung ersetzen.

        sudo apt-get install ocl-icd-libopencl1



## Intel GPU (Beignet)

+   <http://www.freedesktop.org/wiki/Software/Beignet/>
+   <https://01.org/beignet>

<!---->

+   `beignet-opencl-icd`

<!---->

    sudo apt-get install beignet-opencl-icd



### Alternative (from Source)

+   <https://gist.github.com/spiralray/cae0bc235509e495fec1>

<!---->

1.  Das Beignet Git Repository lokal klonen.

        git clone ssh://git.freedesktop.org/git/beignet
2.  Den Tag des letzten Releases auslesen und den Commit auschecken.

        git tag | grep Release_ #z.B. Release_v1.3.1
        git checkout Release_v1.3.1
3.  Die Build Dependencies installieren. Es werden LLVM 3.3 bis 3.6 unterstützt, wobei 3.5 als stabilste Version empfohlen wird. 3.3 und 3.4 werden nur als legacy unterstützt.

        sudo apt-get install cmake pkg-config python ocl-icd-dev ocl-icd-opencl-dev libdrm-dev libxfixes-dev libxext-dev llvm-3.5-dev clang-3.5 libclang-3.5-dev libtinfo-dev libedit-dev zlib1g-dev
4.  Beignet kopillieren. Der Quellcode kann mit GCC 4.6 bis 4.8, CLANG 3.5 und ICC 14.0.3 kompilliert werden, wobei GCC als Standardcompiler empfohlen wird.

        mkdir build
        cd build
        cmake -DCOMPILER=GCC ..
5.  `.deb` Paket erstellen und installieren.

        checkinstall
        sudo dpkg -i beignet_*.deb



#### Einrichtung

+   <http://www.freedesktop.org/wiki/Software/Beignet/#knownissues>

Ob weitere Anpassungen notwendig sind, lässt sich durch [Ausführen der Unit Tests](http://www.freedesktop.org/wiki/Software/Beignet/#howtorun) herausfinden. Dazu einfach folgende Befehle im `build` Verzeichnis ausführen.

    cd utests
    ./setenv.sh
    ./utest_run

Ist die Pass Rate kleiner als 100%, müssen Anpassungen vorgenommen werden.

Einen weiteren Test stellt die [folgende Methode](http://wiki.tiker.net/OpenCLHowTo#Testing) dar.

    curl https://codeload.github.com/hpc12/tools/tar.gz/master | tar xvfz -
    cd tools-master
    make
    ./print-devices

Bei Fehlermeldungen, insbesondere bezüglich des GPU Devices (*platform 1*), sind weitere Schritte notwendig.
Fehlermeldungen wie "drm\_intel\_gem\_bo\_context\_exec() failed: Invalid argument" und "Beignet: warning - disable atomic in L3 feature." kennzeichnen, dass die *register whitelist* deaktiviert werden muss, während "Beignet: self-test failed" und "Beignet: disabling non-working device" ein Indiz dafür sind, dass der Kernel gepatcht werden muss.
Eine fehlerfreie Ausgabe sieht ähnlich wie folgende aus.

    platform 0: vendor 'Intel(R) Corporation'
      device 0: 'Intel(R) Core(TM) i7-4500U CPU @ 1.80GHz'
    platform 1: vendor 'Intel'
      device 0: 'Intel(R) HD Graphics Haswell Ultrabook GT2 Mobile'

+   Unter Linux 3.15 und 3.16, sowie späteren Versionen bei Verwendung von Haswell CPUs, kann es vorkommen, dass nahezu keine Unit Tests erfolgreich abgeschlossen werden. Um dieses Problem zu beheben kann die *register whitelist* deaktiviert werden indem die folgende Zeile ausgeführt wird.

        sudo sh -c "echo 0 > /sys/module/i915/parameters/enable_cmd_parser"

    Sollte dies einige Fehlermeldungen beheben, kann die Konfiguration dauerhaft vorgenommen werden indem der Befehl in die Datei `/etc/rc.local` vor dem `exit` Aufruf eingefügt wird.
+   Bei Verwendung von Haswell CPUs kann bis Linux 4.2 außerdem die Fehlermeldung "Beignet: self-test failed", begleitet von 15 bis 30 fehlgeschlagenen Unit Tests auftreten. Linux Kernels bis Version 4.0 unterstützen auf Haswell CPUs keinen *shared local memory (\_\_local)*. Möglicherweise kann das Problem durch das kompillieren und installieren eines gepatchten Kernels behoben werden. Unter elementary OS 0.3 *Freya* (Ubuntu 14.04 *Trusty Thar*) gelang dies mittels eines modifizierten 3.19 Kernels (`linux-source` aus den Ubuntu 15.04 *Vivid Vervet* Paketquellen). Das Vorgehen für jenen Kernel wird im Folgenden beschrieben (siehe auch [ubuntuusers Wiki](http://wiki.ubuntuusers.de/kernel/kompilierung)).

    1.  Unter *Versions published* auf <https://launchpad.net/ubuntu/vivid/+source/linux> die Version aus dem *Release* wählen (linux 3.19.0-15.15).
    2.  Das `linux-source-3.19.0` Paket unter *Binary packages built by this source* wählen.
    3.  Aus den *Published versions* die *Release* Version für amd64 auswählen (linux-source-3.19.0 3.19.0-15.15).
    4.  Das `.deb` Paket unter *Downloadable files* herunterladen und installieren.

        +   `linux-source-3.19.0`

        <!---->

            sudo dpkg -i linux-source-3.19.0_*.deb
    5.  Zum Kompillieren von Kerneln neuer als 3.13 bzw. ab 3.16 wird außerdem die Version 13.003 von `kernel-package` benötigt (siehe Bug [1308183](https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/1308183)), welches unter Ubuntu 14.04 ebenfalls nicht in den offiziellen Paketquellen enthalten ist. Deshalb kann es [hier](https://launchpad.net/ubuntu/+source/kernel-package/13.003/+build/5980712) heruntergeladen und anschließend installiert werden.

        +   `kernel-package` 13.003

        <!---->

            sudo dpkg -i kernel-package_13.003_all.deb
    6.  Kernel vorbereiten und kompillieren.

            mkdir ~/linux
            cd ~/linux
            wget https://01.org/sites/default/files/disable-batchbuffer-security.patch
            tar xvjf /usr/src/linux-source-3.19.0.tar.bz2
            cd linux-source-3.19.0
            patch drivers/gpu/drm/i915/i915_gem_execbuffer.c < ../disable-batchbuffer-security.patch
            cp /boot/config-`uname -r` .config
            yes "" | make oldconfig
            make-kpkg -j4 --append-to-version "-custom" --initrd buildpackage
    7.  Kernel installieren.

        +   `linux-image-3.19.3-custom`

        <!---->

            sudo dpkg -i linux-image-3.19.3-custom_3.19.3-custom-10.00.custom_amd64.deb
