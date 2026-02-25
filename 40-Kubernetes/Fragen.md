### Kubernetes Grundlagen

**Was ist Kubernetes?**

* Eine Open-Source-Plattform zur Automatisierung der Bereitstellung, Skalierung und Verwaltung von containerisierten Anwendungen (auch K8s genannt).

**Was ist die Hauptaufgabe von Kubernetes?**

* Die Orchestrierung von Containern: Kubernetes stellt sicher, dass die gewünschte Anzahl an Containern läuft, verteilt die Last und verwaltet Ressourcen automatisch.

**Wer ist der Eigentümer von Kubernetes?**

* Ursprünglich von Google entwickelt, gehört es heute der **Cloud Native Computing Foundation (CNCF)**.

---

### Netzwerkstruktur

**Was für eine Netzwerkstruktur verwendet Kubernetes?**

* Ein flaches, Cluster-weites Netzwerk, in dem jeder Pod eine eigene IP-Adresse hat und jeder Pod mit jedem anderen Pod ohne NAT kommunizieren kann.

**Über was kommunizieren die Services von Node zu Node?**

* Über das **Kube-Proxy**-Modul und virtuelle IP-Adressen (ClusterIP), welche den Traffic über das Overlay-Netzwerk an die entsprechenden Pods weiterleiten.

---

### Objekte (Ressourcen)

**In welchem Dateiformat werden Kubernetes Objekte beschrieben?**

* Im **YAML**-Format (manchmal auch JSON).

**Mit welchem CLI Tool werden Objekte verwaltet?**

* Mit dem Befehl **`kubectl`**.

**Mit was lassen sich Kubernetes Objekte gruppieren?**

* Mittels **Labels** (Key-Value-Paare) und **Selectors**.

**Was sind Pods?**

* Die kleinste rechenfähige Einheit in Kubernetes; ein Pod beherbergt einen oder mehrere Container, die sich ein Netzwerk und Speicher teilen.

**Was sind Services?**

* Eine Abstraktion, die eine Gruppe von Pods logisch definiert und eine stabile IP-Adresse/DNS-Namen bereitstellt, um sie im Netzwerk erreichbar zu machen.

**Was ist ein Ingress?**

* Ein Objekt, das den externen Zugriff (HTTP/HTTPS) auf Services innerhalb des Clusters verwaltet (ähnlich einem Reverse Proxy).

**Was sind Namespaces bzw. deren Aufgabe?**

* Virtuelle Cluster innerhalb eines physischen Clusters, um Ressourcen voneinander zu trennen (z.B. für verschiedene Projekte oder Umgebungen wie `prod` und `dev`).

**Was ist die Aufgabe eines ReplicaSets?**

* Es stellt sicher, dass zu jedem Zeitpunkt eine festgelegte Anzahl von identischen Pod-Kopien (Replikaten) läuft.

**Für was können Deployments verwendet werden?**

* Für das deklarative Update von Pods und ReplicaSets (z.B. für Version-Rollouts, Rollbacks und Skalierung).
