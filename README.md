########################################################################################################################################
# M300-Services 
########################################################################################################################################

# Inhaltsvverzeichnis
1. _Einleitung - [Einleitung](#einleitung)
2. _01 - [K1](#k1)
3. _03 - [K3](#k3)
4. _04 - [K4](#k4)
5. _05 - [K5](#k5)

# _Einleitung 
In diesem Modul geht es darum Virtuelle maschinen zu automatisieren. Dies machen wir Virtualbox, Vagrant, Visualstudio und weiteres, in den folgenden Abschnitten werden diese Programme erklärt.


## _K1
# Virtualbox
Virtualbox ist eine Software in der umgebung Virtualisieren. Das ganze Projekt basiert komplett auf Virtualbox.

https://www.virtualbox.org/ - Hier kann man die Software herunterladen

# Vagrant 
Mit der Software Vagrant kann man ganz einfach Virtuelle Maschinen erstellen, dies macht man dann mit verschiedenen Commands

https://www.vagrantup.com/downloads.html - Dies ist der Link zum Download von Vagrant

# Visualstudio-Code 
Visual Studio ist eine Entwicklungsumgebung, mit der man in verschiedenen Programmiersprachen programmieren kann. Visual Studio unterstützt u.a. die Sprachen Visual Basic .NET, C oder C#.

In diesem Projekt verwenden wir Visual Studio zum dokumentieren.

https://visualstudio.microsoft.com/de/ - Hier kann man das Visual Studio herunterladen

# SSH-Key für Client erstellen 
Mit dem Bash kann man den SSH KEy auf den Client installieren. Die nötige Software kann man hier herunterladen: https://git-scm.com/downloads

1. Dies im Bash eingeben.
```
    $  ssh-keygen -t rsa -b 4096 -C "beispiel@beispiel.com
```
2. Mit dem erstellt man neue Keys
```
    Generating public/private rsa key pair
```
3. Hier kann man ein Verzeichnis angeben, mit ENTER kann dies bestätigen

```
    Enter a file in which to save the key (~/.ssh/id_rsa): [Press enter]
```
4. Noch ein Passwort angeben. 
```
    Enter passphrase (empty for no passphrase): [Passwort]
   Enter same passphrase again: [Passwort wiederholen]
```


## _K3 
# Bestehende vm aus Vagrant-Cloud einrichten 
Um eine bestehende VM mit Vagrant einzurichten muss zuerst das Vagrantfile vorhanden sein. Dafür habe ich das Repository "M300" heruntergeladen. Danach bin ich in das Verzeichnis in der GitBash gewechselt wo das Vagrantfile hinterlegt ist und habe die VM mit folgendem Befehl erstellt.
```
    Vagrant up
```

     

# _K4 
# FireWall eingerichtet inkl. Rules 
Die Firewall wurde mit folgenden Befehlen eingerichtet und konfiguriert. Ich habe mich dafür entschieden, dass Port 80 offen ist, damit man auch auf die Website gelangen kann. Auch habe ich den Port 22 geöffnet, damit mit SSh verbunden werden kann. 
```
        #firewall installieren
        sudo apt-get -y install ufw

        #firewall starten
        sudo ufw enable

        #Port 80 öffnen für alle
        sudo ufw allow 80/tcp
        
        #Port 22 öffnen
        sudo ufw allow 22/tcp
```
Möchte man die aktiven FireWall Rules anschauen, kann man das mit einem Befehl machen. 
```
    ~$ sudo ufw status
    Status: active

    To                         Action      From
    --                         ------      ----
    80/tcp                     ALLOW       Anywhere
    22/tcp                     ALLOW       Anywhere
    80/tcp (v6)                ALLOW       Anywhere (v6)
    22/tcp (v6)                ALLOW       Anywhere (v6)
```
# Reverse-Proxy eingerichtet 
Den Reverse Proxy habe ich mit folgdenden Befehlen eingerichtet:  
    
```
    #Proxserver einrichten
    sudo apt-get -y install apache2-bin libxml2-dev
    sudo service apache2 restart
    sudo a2enmod proxy
    sudo service apache2 restart
    sudo a2enmod proxy_html
    sud service apache2 restart
    sudo a2enmod proxy_http

    echo "ServerName localhost" >> /etc/apache2/apache2.conf

    sudo service apache2 restart

    sudo rm /etc/apache2/sites-available/000-default.conf
    sudo touch /etc/apache2/sites-available/000-default.conf
    cat >> /etc/apache2/sites-available/000-default.conf<<EOL
    <VirtualHost *:80>
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html

            <Directory /var/www/html/>
                Options Indexes FollowSymLinks
                AllowOverride All
                Require all granted
            </Directory>

            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined

            <IfModule mod_dir.c>
                DirectoryIndex index.php index.pl index.cgi index.html index.xhtml index.htm
            </IfModule>
                        # Allgemeine Proxy Einstellungen
        ProxyRequests Off
        <Proxy *>
            Order deny,allow
            Allow from all
        </Proxy>

        # Weiterleitungen master
        ProxyPass /master http://master
        ProxyPassReverse /master http://master

    </VirtualHost>
    EOL

```
Mit Cat habe ich mehrere Zeilen Inhalt in die Datei 000-default.conf hinzugefügt. 

# Benutzer- und Rechtevergabe ist eingerichtet 
Ich habe einen zweiten "standard" Benutzer eingerichtet, der nicht zu viele Rechte erhalten sollte. Ausserdem habe ich eine neue Gruppe erstellt, wo all die "standard" Benutzer zugewiesen werden. Zum Test habe ich auch ein File erstellt mit bestimmten Berechtigungen. 

```
    #Neuer Benutzer erstellen mit Home-Directory
    sudo useradd -m oscar

    #Neue Gruppe erstellen
    sudo addgroup --gid 2000 standard_group

    #Benutzer Gruppe hinzufügen
    sudo usermod -aG standard_group oscar
```
Parameter kurz erklärt: 
* useradd erstellt Benutzer
* -m erstellt ein Homeverzeichnis
* --gid erstellt Gruppe mit bestimmter ID
* usermod -aG fügt einen Benutzer in weiteren Gruppen hinzu

# _K5 
# Reflexion 
