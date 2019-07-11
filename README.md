
# M300-Services 

# LB2

# Inhaltsvverzeichnis
1. _Einleitung - [Einleitung](#einleitung)
2. _01 - [_K1.](#k1)
3. _03 - [_K3.](#k3)
4. _04 - [_K4.](#k4)
5. _05 - [_K5.](#k5)

# _Einleitung 
In diesem Modul geht es darum Virtuelle maschinen zu automatisieren. Dies machen wir Virtualbox, Vagrant, Visualstudio und weiteres, in den folgenden Abschnitten werden diese Programme erklärt.


## K1
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


## K3 
# Bestehende vm aus Vagrant-Cloud einrichten 
Um eine bestehende VM mit Vagrant einzurichten muss zuerst das Vagrantfile vorhanden sein. Dafür habe ich das Repository "M300" heruntergeladen. Danach bin ich in das Verzeichnis in der GitBash gewechselt wo das Vagrantfile hinterlegt ist und habe die VM mit folgendem Befehl erstellt.
```
    Vagrant up
```

     

# K4 
# FireWall eingerichtet inkl. Rules 
Die Firewall wurde mit folgenden Befehlen eingerichtet und konfiguriert.
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

# K5

# Wissenzuwachs
Zuvor kannte ich nur Visual Studio, da ich früher mit Programmieren zu tun hatte, jedoch war mein Wissen in Visual Studio gering. Auch mit Github hatte ich zu tun, da es eine sehr praktische Pllattform ist, sich wissen zu erwerben. Es existieren auch sehr praktische Vorlagen wie auch Tutorials die mir früher geholfen haben. Neu kenn ich Vagrant und Git Bash, Git Bash ist nicht allzu anders als Linux Bash. Zudem habe ich noch mehr über Visual Studio gelernt, sowie auch über die Verknüpfung von Visual Studio mit Github, was für mich etwas verwirrend war.

# Reflexion 
Interessantes Thema, jedoch wurde durch meine Faulheit wenig gemacht.

# LB3

1. _Einleitung - [Einleitung](#einleitung)
2. _01 - [K1](#_k1.)
3. _03 - [K3](#_k3.)
4. _04 - [K4](#_k4.)
5. _05 - [K5](#_k5.)
6. _06 - [K6](#_k6.)

## _K1.

Diese Umgebung wurde teilweise auf eigenem Notebook eingericht, sowohl funktioniert es auch teilweise

-VirtualBox
-Vagrant
-Visualstudio-Code
-Git-Client
-SSH-Key für Client erstellt

## [LB2 schon gemacht]

Eine Versionsverwaltung ist für den Github nötig, sowie kann man bei Github dokumente zentral hoch-/herunter-laden

Mit dem Vagrant können wir unsere virtuellen maschinen automatiesert aufsetzen lassen.

Virtualbox ist eine Software in der umgebung Virtualisieren. Das ganze Projekt basiert komplett auf Virtualbox.

https://www.virtualbox.org/ - Hier kann man die Software herunterladen


Visual Studio ist eine Entwicklungsumgebung, mit der man in verschiedenen Programmiersprachen programmieren kann. Visual Studio unterstützt u.a. die Sprachen Visual Basic .NET, C oder C#.

In diesem Projekt verwenden wir Visual Studio zum dokumentieren.

https://visualstudio.microsoft.com/de/ - Hier kann man das Visual Studio herunterladen

## _K2.
Die eigene Lernumgebung ist eingerichtet

-GitHub oder Gitlab-Account ist erstellt
-Git-Client wurde verwendet
-Dokumentation ist als Mark Down vorhanden
-Markdown-Editor ausgewählt und eingerichtet
-Markdown ist strukturiert
-Persönlicher Wissenstand im Bezug auf die wichtigsten   Themen ist dokumentiert (Containerisierung / Docker,    Microservices)


Containerisierung/Container

 Beim Container wird eine Virtualisierungtechnik im Computerumfeld verwendet, die Anwendungen inklusive ihrer Laufzeitumgebungen voneinander trennt. Nicht wie bei einer virtuellen Maschine, beinhaltet der Container kein eigenes Betriebsystem, sondern verwendet es dies vom Host.

Container erstellen wird auch „Virtualisierung der Virtualisierung“ oder „Virtualisierung der nächsten Generation“ genannt, aber die Containerisierung gibt es schon länger aks die Virtualisierung oder dem Aufkommen von modernen Technologien wie Docker und Linux Containers.
## _K3.
## Docker Befehle

Befehl | Bedeutung
docker | build "Source"	Erstellt ein Docker image
docker | exec it "Container" \bin\bash	Exploriert einen Container
docker images | Zeigt alle verfügbare Docker images
docker rmi "image" |Löscht ein Docker image
docker run "image" | startet ein Docker image
Docker installation
TAAPEAA1@U278700 MINGW64 /c/users/TAAPEAA1/Desktop/M300-Services (master) $ vagrant ssh Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.4.0-148-generic x86_64)

-Documentation: https://help.ubuntu.com
-Management: https://landscape.canonical.com
-Support: https://ubuntu.com/advantage

52 packages can be updated. 29 updates are security updates.

New release '18.04.2 LTS' available. Run 'do-release-upgrade' to upgrade to it.

Last login: Mon Jun 17 13:03:57 2019 from 10.0.2.2 vagrant@web:$ docker --version Docker version 18.09.5, build e8ff056 vagrant@web:$

Überprüfen ob Docker installiert ist.

[docker --version]

Ob ein Docker Volume existiert.

[docker container list]

Zugriff auf eigene Dienste möglich.

Im Browser localhost öffnen mit z.B. Port 8080

[localhost:8080]

Firewall Ports offen?

[sudo ufw status]

## Docker installation

1. Zuerst Image erstellen

[docker build -t webserver .]

2. Überprüfen ob es erstell wurde mit folgendem Befehl:

[docker images]

3. Container erstellen. Image  muss man angeben.

[docker run --rm -d --name webserver webserver]

4. Hiermit kann man überprüfen ob der Container läuft:

[docker ps]

Der Webserver war unter der URL:http://localhost:8080 erreichbar.

## Volumen einrichten So erstellt man ein Volumen.

[docker volume create "Name"]


Mit diesem Befehl kann man nachschauen ob das Volume erstellt wurde(dies listet alle volumes auf):
[docker volume ls]

_Sicherheitseinstellungen Docker
Für alle Applikationen kann ein andere Host Port weitergeleitet werden. Es definiert mit der Zeile EXPOSE. Anderweitige Einstellungen können vorgenommen werden, indem man einem User die Berechtigung gibt einen gewissen Container anzupassen. Sonst noch kann man Gruppeneinstellungen vornehmen, damit nur eine gewisse Benutzergruppe einen Container verwalten kann.

## Service Überwachung

Mit verschiedenen Befehlen kann die Docker Container Umgebung überwachen. Zum einen kann man alle Docker Prozesse mittels docker ps anzeigen und falls man alle Container auflisten will, dann gibt es den Befehl Docker Container list. Mit Docker logs zeigt man aktive statistiken eines Containers auf. Zusätzlich zeigt er die stderr und stdout statistiken raus.

## stderr

Stderr (Standardfehler) ist der Standard-Dateideskriptor, mit dem ein Prozess Fehlermeldungen schreiben kann.

In Unix-ähnlichen Betriebssystemen wie Linux durch den POSIX-Standard definiert..

Im Terminal wird der Standardfehler standardmässig auf dem Bildschirm des Benutzers angezeigt.

## stdout

Stdout (Standardausgabe) ist der Standard-Dateideskriptor, mit dem ein Prozess die Ausgabe schreiben kann.

Im Terminal wird die Standardausgabe standardmässig auf dem Bildschirm des Benutzers angezeigt.

## _K5.
Wir haben schon in ÜKs mit Container zu tun, es ist nicht wirklich komplex zum verstehen, aber kann einen noch recht schnell verwirren wenn man es falsch erklärt bekommt. Der Rest ist eigentlich recht neu für mich, man hört von 1 oder 2 dingen, aber verstehen ist ein anderer Bereich.

## Fazit

Ein recht interessantes Thema, eigentlich etwas sehr wichtiges das man erlernen sollte, leider hatte ich nicht so viel Zeit investiert, sowie auch meinen Kopf richtig verwendet. Ist wirklich empfehlenswert zum weiter führen.

## _K6.
Image Bereitstellung Beispiel von mc-b/m300

FROM ubuntu:14.04

RUN apt-get update
RUN apt-get -q -y install apache2 

# Konfiguration Apache
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

RUN mkdir -p /var/lock/apache2 /var/run/apache2

EXPOSE 80

VOLUME /var/www/html

CMD /bin/bash -c "source /etc/apache2/envvars && exec /usr/sbin/apache2 -DFOREGROUND"
