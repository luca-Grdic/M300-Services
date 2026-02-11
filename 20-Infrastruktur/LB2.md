Dokumentation LB2 Hands-on: Webalizer Automatisierung

Mein Vorgehen
Zuerst habe ich lokal ein neues Verzeichnis myVM erstellt und eine Standard-VM mit Ubuntu Xenial initialisiert, um die Befehle manuell zu testen. Nach dem Login via vagrant ssh habe ich die Paketquellen aktualisiert und die benötigten Dienste Apache2 und Webalizer installiert.

Manueller Test:

sudo apt-get update

sudo apt-get install -y apache2

sudo apt-get install -y webalizer



Problemanalyse und Feintuning
Beim manuellen Testen sind mir folgende Probleme aufgefallen, die ich für die Automatisierung lösen musste:

Verzeichnis-Fehler: Webalizer schreibt seine Daten standardmäßig nach /var/www/webalizer, Apache erwartet sie unter Ubuntu aber in /var/www/html/webalizer.

Keine Daten: Ohne Web-Traffic bleibt die Statistik leer.

Log-Rotation: Webalizer wertet oft nur archivierte Logs aus, weshalb ein manueller Log-Rotate nötig ist.

Die fertige Automatisierung (Vagrantfile)
Ich habe alle Befehle und Fixes in das Vagrantfile übertragen. Das Provisioning-Skript übernimmt nun folgende Aufgaben automatisch:

Installation von Apache und Webalizer.

Erzeugung von künstlichem Traffic via curl.

Korrektur der Pfade in der webalizer.conf mittels sed.

Erzwingen der Log-Rotation und Ausführung des Analyse-Cronjobs.

![Vagrantfile](vagrantfile.png)

Resultat
Nach dem Befehl vagrant up ist der Dienst komplett konfiguriert. Die Statistiken können direkt über den Host-Browser aufgerufen werden.

Erfolgreicher Aufruf der Statistik:

URL: http://localhost:8080/webalizer/

![Ergebnis](Ergebnis.png)