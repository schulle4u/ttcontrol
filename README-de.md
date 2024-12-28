<p align="right"><a href="README-de.md">Deutsch</a> &nbsp; <a href="README.md">English</a></p>

# TTControl
Steuert mehrere Serverinstanzen der Sprachkonferenz-Software TeamTalk.

## Einleitung

Da es bisher kaum öffentlich zugängliche Werkzeuge zur Verwaltung insbesondere von multiplen TeamTalk-Servern auf einem system gibt, stelle ich hier mein eigenes, bescheidenes Script zur Verfügung. Dieses Shell-Script bietet Funktionen zum Steuern einer oder mehrerer TeamTalk-Serverinstanzen an. Es werden die üblichen Befehle zum Starten, neu starten, Stoppen und Abfragen des Status bereitgestellt. Des Weiteren kann die Verzeichnisstruktur für einen neuen Server angelegt und an den Einrichtungsassistenten übergeben werden. Das finale Setup sieht vor, dass jeder Server in seinem eigenen Arbeitsverzeichnis läuft. 

## Installation

Auf einem frisch eingerichteten System kannst du einfach das Repository clonen oder herunterladen. Führe danach `sudo ./install` aus, um ttcontrol mit dem empfohlenen Einstellungen einzurichten. In einer bestehenden TeamTalk-Infrastruktur solltest du die unten beschriebenen Schritte manuell ausführen und deine Pfade entsprechend anpassen. 

## Empfohlene Einrichtung

1. Den [TeamTalk-Server](https://bearware.dk) herunterladen und installieren.
2. Einen Systembenutzer für den TeamTalk-Server anlegen: `sudo useradd -r -s /bin/false teamtalk`
3. Ein Hauptverzeichnis für die Serverkonfigurationen anlegen, z. B. `sudo mkdir -p /var/lib/teamtalk/servers`
4. Zugriffsrechte und Eigentümer für das TeamTalk-Verzeichnis setzen: `sudo chmod -R 774 /var/lib/teamtalk && sudo chown -R teamtalk:teamtalk /var/lib/teamtalk`
5. Repository clonen oder in ein beliebiges Verzeichnis [herunterladen](https://github.com/schulle4u/ttcontrol/archive/refs/heads/main.zip).
6. Optional: In der Datei `ttcontrol.conf` die Konfiguration wie gewünscht anpassen.
7. Falls noch nicht vorhanden, einen neuen Server anlegen: `sudo ./ttcontrol create Servername`
8. Alle Server starten: `sudo ./ttcontrol start`

## Konfiguration

TTControl sucht unter `/etc/ttcontrol.conf` oder im eigenen Skriptverzeichnis nach der Konfigurationsdatei. Falls keine Datei gefunden wird, werden Standardwerte des Skripts verwendet. Die folgenden Optionen können angepasst werden: 

* `tt_bin` = Pfad zur Binärdatei des TeamTalk-Servers (Standard: `/usr/local/bin/tt5srv`).
* `server_dir` = Pfad zum Hauptverzeichnis der Serverkonfigurationen, hier werden die jeweiligen Unterverzeichnisse angelegt (Standard: `/var/lib/teamtalk/servers`).
* `tt_user` = Benutzer, unter welchem die TeamTalk-Server laufen sollen (Standard: `teamtalk`).

## Syntax
`sudo ./ttcontrol {start|stop|restart|status|create|clean} {server_name}`

Folgende Befehle werden unterstützt: 

* `start {Server_name}`: Einen oder alle Server starten.
* `stop` {Server_name}`: Einen oder alle Server stoppen.
* `restart {Server_name}`: Einen oder alle server neu starten.
* `status {Server_name}`: Zustand eines oder aller Server abfragen.
* `create {server_name}`: Neuen Server erstellen, ein servername muss angegeben werden.
* `clean {Server_name}`: Einen oder alle Server von überflüssigen Dateien bereinigen.

## Entwicklung
Copyright (C) 2024 Steffen Schultz, freigegeben unter den Bedingungen der MIT-Lizenz: Diese Software steht in keinerlei Verbindung zu TeamTalk oder sonstigen von BearWare.dk entwickelten Produkten. Nutzung auf eigene Verantwortung! 