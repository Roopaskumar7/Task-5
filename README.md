

````markdown
# 🐳 Kubernetes Minikube Tutorial

This project demonstrates how to **deploy and manage a simple web application** on a local **Kubernetes cluster using Minikube**.

---

## 🎯 Objective

- Set up Minikube and Kubernetes locally.
- Deploy a web application using a `deployment.yaml`.
- Expose the app using a `service.yaml`.
- Manage and scale deployments using `kubectl`.

---

## 🛠 Tools Required

- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Docker](https://www.docker.com/) (optional if using local images)

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/emailtovamos/kubernetes-minikube-tutorial.git
cd kubernetes-minikube-tutorial
````

---

### 2. Start Minikube

```bash
minikube start
```

---

### 3. Deploy the Application

Apply the deployment YAML:

```bash
kubectl apply -f deployment.yaml
```

---

### 4. Expose the Application

Apply the service YAML:

```bash
kubectl apply -f service.yaml
```

---

### 5. Access the Application

```bash
minikube service my-service
```

This command will open the application in your browser.

---

## 📦 YAML Files

### `deployment.yaml`

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 1
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app
        image: nginx
        ports:
        - containerPort: 80
```

---

### `service.yaml`

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: NodePort
```

---

## 🔧 Managing the App

### View Pods and Services

```bash
kubectl get pods
kubectl get services
```

### Scale the Deployment

```bash
kubectl scale deployment my-app --replicas=3
```

### Describe and Logs

```bash
kubectl describe deployment my-app
kubectl logs <pod-name>
```

---

## 📸 Deliverables (Take Screenshots)

* [ ] Pods (before and after scaling)
* [ ] Services
* [ ] App running in browser
* [ ] `kubectl describe` and `kubectl logs` output


