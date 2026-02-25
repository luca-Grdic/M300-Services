## Protokollieren & Überwachen

**Warum sollten Container überwacht werden?**

* Um Fehler, Performance-Engpässe oder ungewöhnliche Ressourcenbelastungen frühzeitig zu erkennen und die Verfügbarkeit des Dienstes zu garantieren.

**Was ist das syslog und wo ist es zu finden?**

* Es ist das zentrale Protokollierungssystem eines Linux-Hosts. Die Log-Dateien befinden sich im Verzeichnis `/var/log` (z. B. `/var/log/syslog` oder `/var/log/messages`).

**Was ist stdout, stderr, stdin?**

* **stdin:** Standard-Eingabe (Datenfluss *in* das Programm).
* **stdout:** Standard-Ausgabe (normale Programmausgaben).
* **stderr:** Standard-Fehlerausgabe (spezieller Kanal für Fehlermeldungen).

---

## Container sichern & beschränken

**Verhinderung von `docker run -v /:/homeroot ...` durch normale User**

* Zugriff auf den Docker-Daemon einschränken: Nur der User `root` oder Mitglieder der Gruppe `docker` dürfen Container starten. Idealerweise wird der Zugriff für normale Benutzer komplett unterbunden.

**Wie können verschiedene Mandanten getrennt werden?**

* Die sicherste Trennung erfolgt durch den Einsatz separater **Virtueller Maschinen (VMs)**, da diese eine stärkere Isolierung (eigener Kernel) als Container bieten.

**Wie kann der Ressourcenverbrauch von Containern eingeschränkt werden?**

* Durch **Resource Constraints** in Docker (Flags wie `--memory` oder `--cpus`), die den Zugriff auf Hardware-Ressourcen limitieren.

---

## Kontinuierliche Integration (CI)

**Welche Funktionen kann Jenkins übernehmen?**

* Automatisierung von Software-Builds, Durchführung von Modultests (Unit-Tests), Ausführung von Batch-Jobs und Überwachung von Logfiles.

**Wie baut man Modultests?**

* Durch das Erstellen von Test-Skripten (z. B. via **Bash**, Python oder Frameworks wie JUnit), die automatisiert prüfen, ob eine Funktion das erwartete Ergebnis liefert.

**Wie könnten Jenkins Jobs ausser manuell oder zeitgesteuert gestartet werden?**

* Durch **Webhooks** (automatisch bei einem `git push` in das Repository) oder durch **Triggers**, die von anderen erfolgreich abgeschlossenen Jobs ausgelöst werden.
