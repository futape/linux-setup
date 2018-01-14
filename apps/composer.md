# Composer

+	<https://getcomposer.org>
+	<https://getcomposer.org/doc/faqs/how-to-install-composer-programmatically.md>



## Installation

+	Composer

<!---->

1.	Zuerst ein eventuell installiertes `composer` Paket deinstallieren:

		sudo apt-get remove composer
2.	Anschließend den Installer herunterladen, die Checksum vergleichen und Composer installieren:

		php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
		php -r "copy('https://composer.github.io/installer.sig', 'composer-setup.sig');"
		php -r "if (hash_file('SHA384', 'composer-setup.php') === trim(file_get_contents('composer-setup.sig'))) { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); unlink('composer-setup.sig'); } echo PHP_EOL;"
		sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
		php -r "unlink('composer-setup.php'); unlink('composer-setup.sig');"



### Alternative

+	`composer`

<!---->

	sudo apt-get install composer
