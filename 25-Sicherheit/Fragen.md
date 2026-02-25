### Firewall und Reverse Proxy

**Unterschied Web Server vs. Reverse Proxy**

* **Web Server:** Liefert Inhalte (Webseiten/Files) direkt aus.
* **Reverse Proxy:** Steht vor dem Server, verteilt Anfragen (Load Balancing) und verbirgt die interne Infrastruktur zur Sicherheit.

**Was ist eine "White List"?**

* Ein Sicherheitskonzept, bei dem alles verboten ist, ausser den explizit erlaubten Adressen oder Programmen.

**Alternative zur Firewall auf jedem Server**

* Zentrale Netzwerk-Firewalls (Gateways) oder **Security Groups** auf Cloud-Ebene, die den Traffic vor Erreichen der Server filtern.

---

### SSH (Secure Shell)

**Unterschied `id_rsa` vs. `id_rsa.pub**`

* **`id_rsa`:** Privater Schlüssel (bleibt geheim auf deinem PC).
* **`id_rsa.pub`:** Öffentlicher Schlüssel (wird auf dem Zielserver hinterlegt).

**Wo darf ein SSH-Tunnel nicht angewendet werden?**

* Zur Umgehung von Firmen-Sicherheitsrichtlinien (Firewall-Bypassing) oder in Umgebungen, in denen verschlüsselter Traffic zwecks Malware-Prüfung kontrolliert werden muss.

**Zweck der Datei `authorized_keys**`

* Speichert die öffentlichen Schlüssel (`.pub`) auf dem Zielserver, damit berechtigte User sich ohne Passwort einloggen können.

**Zweck der Datei `known_hosts**`

* Speichert die Fingerprints (Identität) der besuchten Server, um "Man-in-the-Middle"-Angriffe durch Warnmeldungen bei Schlüsseländerungen zu verhindern.
