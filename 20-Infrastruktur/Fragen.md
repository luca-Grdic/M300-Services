# Fragen und Antworten zu Cloud Computing & Vagrant

## Cloud Computing

**Was versteht man unter Cloud-Computing?**

> Darunter versteht man die Nutzung von IT-Infrastruktur und Programmen, die nicht auf dem eigenen lokalen Rechner installiert sind, sondern auf entfernten Servern ausgeführt und über das Netzwerk (meist das Internet) aufgerufen werden.

**Was versteht man unter Infrastructure as a Service (IaaS)?**

> IaaS bildet die unterste Ebene des Cloud-Computings. Der Anbieter stellt die Hardware-Ressourcen bereit, während der Benutzer seine Instanzen (wie virtuelle Maschinen) selbst aufsetzt und das Betriebssystem sowie die Software weitestgehend eigenständig verwaltet.

---

## Infrastructure as Code (IaC)

**Was ist der Hauptunterschied zur manuellen Installation einer VM?**

> Die wesentlichen Vorteile liegen in der vollständigen **Automatisierung**, der exakten **Wiederholbarkeit** des Setups und der integrierten **Dokumentation** durch den Code.

---

## Vagrant

**Was wird mit Vagrant erzeugt?**

> Es werden virtuelle Maschinen (VMs) erzeugt und verwaltet.

**Welche der Aussagen treffen zu?**

* a) Vagrant ist ein HyperVisor.
* **b) Vagrant erzeugt virtuelle Maschinen; dabei werden mehrere HyperVisor und Cloud-Umgebungen (z. B. AWS) unterstützt.**
* c) Vagrant erzeugt Container.

> **Antwort:** b) ist korrekt.

**In welchen Bereich des Cloud-Computings ist Vagrant einzuordnen: IaaS, PaaS oder SaaS?**

> Vagrant ist im Bereich **IaaS** (Infrastructure as a Service) einzuordnen.

**Welche Alternativen zu Vagrant bestehen?**

> Eine Übersicht bekannter Alternativen findest du hier: [AlternativeTo - Vagrant](https://alternativeto.net/software/vagrant/)

**Wo speichert Vagrant seine Konfiguration?**

> Die gesamte Konfiguration wird im sogenannten **Vagrantfile** gespeichert.

**Was bedeutet die Fehlermeldung: "A Vagrant environment or target machine is required to run this command."?**

> Diese Meldung besagt, dass der Befehl in einem Verzeichnis ausgeführt wurde, in dem keine gültige `Vagrantfile`-Konfiguration vorhanden ist.

**Bei welcher LPI-Zertifizierung nützt mir das Wissen über Vagrant?**

> Das Wissen ist besonders wertvoll für die Zertifizierung zum [LPI DevOps Tools Engineer](https://www.lpi.org/our-certifications/devops-overview).