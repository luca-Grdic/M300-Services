# Dokumentation LB3: Docker Hands-on

## 1. Installation und Fehlerbehebung (Troubleshooting)
Mein Ziel war es, eine Docker-Umgebung mit Vagrant aufzusetzen. Dabei trat direkt zu Beginn ein Fehler bei der Installation auf: Die GPG-Keys für die Docker-Paketquellen waren veraltet, weshalb die automatische Installation abbrach.

**Lösung:**
Ich habe das `Vagrantfile` angepasst und die Installation manuell über ein Shell-Skript definiert. Dabei wurden die GPG-Keys manuell hinzugefügt und das stabile Docker-Repository für Ubuntu Xenial eingebunden.

> ![Vagrantfile](Vagrantfile.png)

## 2. Funktionstest (Hello-World)
Nachdem das Vagrantfile angepasst wurde, lief `vagrant up` fehlerfrei durch. Um zu prüfen, ob Docker korrekt funktioniert, habe ich mich per SSH in die VM eingeloggt und den Standard-Testcontainer gestartet.

**Befehl:**
`sudo docker run hello-world`

> ![Hello-World](Hello-world.png)

## 3. Automatisierte Container-Kombination (Ghost & MySQL)
Durch die Konfiguration im `Vagrantfile` wurden beim Start der VM automatisch zwei Container erstellt und miteinander verknüpft:
1. Eine MySQL-Datenbank als Backend.
2. Ein Ghost-Blog als Frontend.

Ich habe getestet, ob die Automatisierung funktioniert hat, indem ich vom Browser meines Laptops auf den Dienst zugegriffen habe.

**Ergebnis:**
Der Blog ist unter `http://localhost:2368/` erreichbar. Dies beweist, dass die Container laufen und das Port-Forwarding sowie die Verknüpfung der Container korrekt konfiguriert wurden.

> ![Ghost Blog](Ghost-Blog.png)

