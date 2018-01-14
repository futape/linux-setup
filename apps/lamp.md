# LAMP-Stack

+	<https://wiki.ubuntuusers.de/LAMP/>
+	**[Apache](https://wiki.ubuntuusers.de/Apache_2.4/):**
	+	<https://wiki.ubuntuusers.de/Apache/Module/>
	+	<https://wiki.ubuntuusers.de/Apache/mod_rewrite/>
	+	<https://wiki.ubuntuusers.de/Apache/Virtual_Hosts/>
+	<https://wiki.ubuntuusers.de/MySQL/>
+	<https://wiki.ubuntuusers.de/PHP/>
+	<https://wiki.ubuntuusers.de/MySQL/Werkzeuge/#phpMyAdmin>
+	<http://www.decocode.de/?37>



## Installation

+	`apache2`
+	`mysql-server` (Installiert `mysql-server-5.7`)
+	`php` (Installiert `php7.0`)
+	`php-cli` (Installiert `php7.0-cli`)
+	`libapache2-mod-php` (Installiert `libapache2-mod-php7.0`)
+	`php-mysql` (Installiert `php7.0-mysql`)
+	`php-imagick`
+	`php-mbstring` (Installiert `php7.0-mbstring`)
+	`php-zip` (Installiert `php7.0-zip`)
+	`phpmyadmin`

<!---->

	sudo apt-get install apache2 mysql-server php php-cli libapache2-mod-php php-mysql php-imagick php-mbstring php-zip phpmyadmin



## Einrichtung

1.	Apache läuft unter dem Nutzer `www-data`. Damit dieser und der eigene Nutzer Schreibzugriff auf das *htdocs* Verzeichnis haben, müssen die Rechte dieses Verzeichnisses angepasst werden:

		sudo chown -R www-data:www-data /var/www
		sudo adduser $USER www-data
		newgrp - www-data
2.	Apache Module aktivieren:

		sudo a2enmod php7.0
		sudo a2enmod rewrite
3.	PHP Module aktivieren:

		sudo phpenmod mysqlnd mysqli pdo_mysql imagick mbstring zip
3.	Apache neustarten:

		sudo service apache2 restart



## Virtual Hosts einrichten

Unter `/etc/apache2/sites-available` eine neue `.conf` Datei mit folgendem Inhalt erstellen (oder die Datei `000-default.conf` als Vorlage kopieren):

	<VirtualHost *:80>
		ServerName domain.local
		DocumentRoot /path/to/documentroot
	</VirtualHost>

Sollen in dem Verzeichnis `.htaccess` Dateien benutzt werden, müssen mittels `AllowOverride` für das Verzeichnis noch Direktiven freigeschaltet werden. Dazu fügt man in dem Virtual Host folgendes ein (um alle - `ALL` - Direktiven freizuschalten):

	<Directory /path/to/documentroot>
		AllowOverride All
	</Directory>

Mittels `ErrorLog` und `CustomLog` kann außerdem noch der Speicherort der Log-Files angepasst werden.

`/path/to/documentroot` und `domain.local` sind stets anzupassen.

Zuletzt muss der Virtual Host noch aktiviert werden:

	sudo a2ensite <filename> # z.B. `sudo a2ensite domain`

Außerdem muss der Name des Virtual Host noch lokal bekannt gemacht werden. Dazu ist in der Datei `/etc/hosts` hinter `localhost` der Virtual Host Name hinzuzufügen oder in einer neuen Zeile zu ergänzen. Z.B. `127.0.0.1 localhost domain.local`.

>	Wenn man die Seite default mit a2dissite deaktiviert hat, ist sicher zu stellen, dass es eine NameVirtualHost Anweisung gibt!
>
>	(<https://wiki.ubuntuusers.de/Apache/Virtual_Hosts/#Administration>)
