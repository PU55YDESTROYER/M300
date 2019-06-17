
# M300-Services 


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

# _K5

#Wissenzuwachs
Zuvor kannte ich nur Visual Studio, da ich früher mit Programmieren zu tun hatte, jedoch war mein Wissen in Visual Studio gering. Auch mit Github hatte ich zu tun, da es eine sehr praktische Pllattform ist, sich wissen zu erwerben. Es existieren auch sehr praktische Vorlagen wie auch Tutorials die mir früher geholfen haben. Neu kenn ich Vagrant und Git Bash, Git Bash ist nicht allzu anders als Linux Bash. Zudem habe ich noch mehr über Visual Studio gelernt, sowie auch über die Verknüpfung von Visual Studio mit Github, was für mich etwas verwirrend war.

# Reflexion 
Interessantes Thema, jedoch wurde durch meine Faulheit wenig gemacht.