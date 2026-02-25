# Dokumentation: Kubernetes Hands-on (Pod & Service Deployment)

## 1. Einleitung und Zielsetzung

In diesem Projekt wird die Bereitstellung eines Webservers (Apache `httpd`) innerhalb eines Kubernetes-Clusters demonstriert. Das Ziel ist der Übergang von der imperativen Steuerung (Direktbefehle via CLI) zur deklarativen Steuerung (Konfiguration via YAML-Dateien).

**Kernkomponenten:**

* **Pod:** Die kleinste Einheit, die den Apache-Container beherbergt.
* **Service (LoadBalancer):** Macht den Webserver über eine Cluster-IP nach aussen erreichbar.

## 2. Infrastruktur und Vorbereitung

Die Umgebung basiert auf dem Projekt `lernkube`.

* **Cluster-IP:** `192.168.60.100` (Beispiel aus Initialisierung)
* **Ressourcen:** Erfordert min. 16 GB RAM und 40 GB HD.
* **Umgebung:** Zugriff vom Host (Windows) via PowerShell (`kubeps.bat`) oder direkt in der VM via `vagrant ssh master-01`.

## 3. Imperative Erstellung (Schritt für Schritt)

Zuerst werden die Ressourcen direkt über `kubectl` erzeugt, um die Funktionsweise zu verstehen.

### 3.1 Namespace erstellen

Um die Umgebung sauber zu halten, wird ein Namespace `test` angelegt:

```bash
kubectl create namespace test

```

### 3.2 Pod starten

Ein Apache-Pod wird erzeugt. Die Option `--restart=Never` verhindert die Erstellung eines Deployments und erzeugt lediglich einen nackten Pod:

```bash
kubectl run apache --image=httpd --restart=Never --namespace test

```

### 3.3 Service exposen

Damit der Apache-Server erreichbar wird, wird ein Service vom Typ `LoadBalancer` erstellt. Kubernetes mappt Port 80 automatisch auf einen freien NodePort:

```bash
kubectl expose pod/apache --type="LoadBalancer" --port 80 --namespace test

```

---

## 4. Deklarative Methode (YAML-Dateien)

Der professionelle Weg in Kubernetes ist die Verwendung von YAML-Dateien. Diese wurden aus den laufenden Ressourcen exportiert (`-o yaml`) und auf die wesentlichen Parameter reduziert.

### 4.1 Die Konfigurationsdateien

**apache-pod.yaml**

```yaml
apiVersion: v1
kind: Pod
metadata:
  labels:
    app.kubernetes.io/name: apache
  name: apache
spec:
  containers:
  - image: httpd
    name: apache

```

**apache-service.yaml**

```yaml
apiVersion: v1
kind: Service
metadata:
  labels:
    app.kubernetes.io/name: apache
  name: apache
spec:
  ports:
  - port: 80
    protocol: TCP
    targetPort: 80
  selector:
    app.kubernetes.io/name: apache
  type: LoadBalancer

```

### 4.2 Anwendung der Konfiguration

Die Ressourcen werden nun in einem neuen Namespace `yaml` mittels des `apply`-Befehls gestartet:

```bash
kubectl create namespace yaml
kubectl apply -f apache -n yaml

```

---

## 5. Verifizierung und Zugriff

Um den Erfolg der Bereitstellung zu prüfen, werden die Ressourcen aufgelistet:

### Zugriff auf den Webserver

Die URL für den Zugriff kann automatisiert ermittelt werden. Dabei wird die API-Server-URL genommen und der Port durch den NodePort des Apache-Services ersetzt:

```bash
kubectl config view -o=jsonpath='{ .clusters[0].cluster.server }' | sed -e 's/https:/http:/' -e "s/6443/$(kubectl get service --namespace yaml apache -o=jsonpath='{ .spec.ports[0].nodePort }')/"

```

---

## 6. Fazit und Erkenntnisse

* **Abstraktion:** Kubernetes wandelt jeden CLI-Befehl intern in eine YAML-Struktur um.
* **Entkopplung:** Durch das Weglassen des Namespaces in den YAML-Dateien können dieselben Definitionen flexibel in verschiedenen Umgebungen (Namespaces) wiederverwendet werden.
* **Automatisierung:** Mit `kubectl apply -f [Verzeichnis]` können ganze Anwendungslandschaften mit einem einzigen Befehl hochgefahren werden.

---

### Tipps für deine Präsentation:

1. Erwähne den **Dashboard Token**, den du beim Start erhalten hast – er ist dein "Passwort" für die grafische Oberfläche.
2. Erkläre kurz den Unterschied zwischen **Cluster-IP** (intern) und dem **NodePort** (extern über die Host-IP erreichbar).
3. Betone, dass **Labels** in der YAML-Datei die Brücke zwischen Pod und Service schlagen (`selector`).

**Möchtest du noch ein kurzes "Glossar" der wichtigsten k8s-Begriffe für das Ende der Doku?**