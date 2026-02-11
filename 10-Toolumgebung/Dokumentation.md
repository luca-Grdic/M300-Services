# Dokumentation: Mein Aufbau der virtuellen Infrastruktur

Für dieses Projekt habe ich lokal den Arbeitsordner `m300-arbeit/erste-vm` erstellt. Dieser diente mir als Basis für die gesamte Konfiguration und die Steuerung meiner virtuellen Umgebung.

## Meine Durchführung der Installation

Die Bereitstellung der Infrastruktur habe ich vollständig automatisiert über das Terminal mit den folgenden Befehlen durchgeführt:

* **vagrant init ubuntu/xenial64**: Mit diesem Befehl habe ich die offizielle Konfigurationsvorlage für Ubuntu 16.04 heruntergeladen und das Vagrantfile erstellt.
* **vagrant up**: Damit habe ich den Prozess in VirtualBox gestartet, das Image geladen und die virtuelle Maschine (VM) hochgefahren.
* **vagrant ssh**: Damit habe ich eine sichere Verbindung zur Kommandozeile der VM aufgebaut, um das System zu administrieren.

## Kontrolle in VirtualBox

In der grafischen Oberfläche von VirtualBox habe ich kontrolliert, ob meine Maschine erfolgreich registriert wurde. Der Status stand auf «läuft», was mir bestätigte, dass die Kommunikation zwischen Vagrant und der Virtualisierungssoftware einwandfrei funktioniert.

![VM in Virtualbox](Virtualbox.png)

## Meine Systemprüfung (Verifizierung)

Nachdem ich mich via SSH eingeloggt hatte, prüfte ich die Systemressourcen der VM. So stellte ich sicher, dass die VM korrekt partitioniert wurde und mir genügend Ressourcen zur Verfügung stehen.

**Meine ausgeführten Befehle:**

* `df -h`: Zeigt mir die aktuelle Festplattenbelegung in lesbarer Form an.
* `free -m`: Gibt mir Auskunft über den verfügbaren Arbeitsspeicher (RAM).

## Meine Konfiguration (Vagrantfile)

Um die Installation von Software zu automatisieren, habe ich mein `Vagrantfile` angepasst. Durch das Hinzufügen eines Shell-Skripts wird der Apache-Webserver beim Start der Maschine automatisch installiert (Provisioning), was mir manuelle Schritte erspart.

![Vagrantfile](Vagrantfile.png)

## Meine Verifizierung (Erfolgskontrolle)

Nach dem erfolgreichen Start der VM habe ich die Funktion des Webservers geprüft. Dank der von mir im Vagrantfile konfigurierten Port-Weiterleitung konnte ich den Apache-Server unter `http://localhost:8080` auf meinem Laptop aufrufen. Das Erscheinen der Standardseite bestätigte mir den Erfolg meiner gesamten Konfiguration.

![Webserver](Webserver.png)