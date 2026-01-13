Perfect Awdhesh. Here is your **all-in-one Kubernetes Markdown Bible**
Commands + explanations + **every YAML type** you will use in real DevOps and Microservices.

You can paste this into `kubernetes.md` and use it as your personal DevOps grimoire 📜🐳

---

# 🧠 Kubernetes Complete Guide (Commands + YAML)

---

# 🧩 What is Kubernetes?

Kubernetes (K8s) is a **container orchestration engine** that:

* Runs containers
* Heals them when they crash
* Scales them
* Connects them
* Exposes them to the internet

Docker is the **ship** 🚢
Kubernetes is the **harbor master** ⚓

---

# 🏗 Kubernetes Architecture

| Component   | Role           |
| ----------- | -------------- |
| Master Node | Brain          |
| Worker Node | Muscle         |
| Pod         | Smallest unit  |
| Container   | App            |
| Deployment  | Controls Pods  |
| Service     | Network        |
| ConfigMap   | Config         |
| Secret      | Passwords      |
| Ingress     | Public gateway |
| Volume      | Storage        |

---

# 🧨 KUBECTL – The Magic Wand

```bash
kubectl version
kubectl cluster-info
kubectl get nodes
kubectl get all
kubectl get pods
kubectl get svc
kubectl get deployments
kubectl get namespaces
```

---

# 📦 Pod Commands

```bash
kubectl get pods
kubectl describe pod mypod
kubectl logs mypod
kubectl exec -it mypod -- bash
kubectl delete pod mypod
```

---

# 🚀 Deployment Commands

```bash
kubectl get deploy
kubectl describe deploy jobms
kubectl scale deploy jobms --replicas=3
kubectl rollout status deploy jobms
kubectl rollout history deploy jobms
kubectl rollout undo deploy jobms
```

---

# 🔥 Apply / Delete YAML

```bash
kubectl apply -f pod.yaml
kubectl apply -f deployment.yaml
kubectl apply -f .

kubectl delete -f pod.yaml
kubectl delete -f .
```

---

# 🌐 Service Commands

```bash
kubectl get svc
kubectl describe svc jobms-service
kubectl expose deploy jobms --type=NodePort --port=8080
```

---

# 🧬 Namespace

```bash
kubectl create namespace dev
kubectl get ns
kubectl apply -f myfile.yaml -n dev
```

---

# 📦 POD YAML

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
    - name: app
      image: nginx
      ports:
        - containerPort: 80
```

---

# 🚀 Deployment YAML

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: jobms
spec:
  replicas: 3
  selector:
    matchLabels:
      app: jobms
  template:
    metadata:
      labels:
        app: jobms
    spec:
      containers:
        - name: jobms
          image: awdhesh9211/jobms:latest
          ports:
            - containerPort: 8080
```

---

# 🌐 Service YAML

```yaml
apiVersion: v1
kind: Service
metadata:
  name: jobms-service
spec:
  type: NodePort
  selector:
    app: jobms
  ports:
    - port: 80
      targetPort: 8080
      nodePort: 30001
```

---

# 🔑 ConfigMap YAML

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  DB_HOST: postgres
  DB_PORT: "5432"
```

---

# 🔐 Secret YAML

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: db-secret
type: Opaque
data:
  username: YWRtaW4=
  password: MTIzNA==
```

(Base64 encoded)

---

# 📂 Volume (PersistentVolume)

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: mypv
spec:
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/data"
```

---

# 📂 PersistentVolumeClaim

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mypvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```

---

# 🌍 Ingress

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
spec:
  rules:
    - host: myapp.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: jobms-service
                port:
                  number: 80
```

---

# ⚙️ Environment Variable from ConfigMap

```yaml
env:
  - name: DB_HOST
    valueFrom:
      configMapKeyRef:
        name: app-config
        key: DB_HOST
```

---

# 🔥 Troubleshooting Commands

```bash
kubectl describe pod mypod
kubectl logs mypod
kubectl get events
kubectl get endpoints
kubectl exec -it mypod -- sh
```

---
