# Download and Install Prometheus and Grafana

## 1. Install Prometheus

### Using Docker
To install Prometheus using Docker, follow these steps:

1. **Pull the Prometheus Docker image**:
   ```sh
   docker pull prom/prometheus
   ```
2. **Run the Prometheus container**:
   ```sh
   docker run -d --name=prometheus -p 9090:9090 prom/prometheus
   ```
3. **Verify that the container is running**:
   ```sh
   docker ps
   ```
4. **Access Prometheus Web UI**:
   - Open your browser and go to: `http://localhost:9090`

### Using Helm
To install Prometheus using Helm, follow these steps:

1. **Add the Prometheus Helm repository**:
   ```sh
   helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
   ```
2. **Update Helm repositories**:
   ```sh
   helm repo update
   ```
3. **Install Prometheus using Helm**:
   ```sh
   helm install prometheus prometheus-community/prometheus
   ```
4. **Check the running services**:
   ```sh
   kubectl get svc
   ```
5. **Expose Prometheus service**:
   ```sh
   kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=prometheus-server-ext
   ```
6. **Retrieve service details**:
   ```sh
   kubectl get svc prometheus-server-ext -n default
   ```
7. **Get Minikube IP**:
   ```sh
   minikube ip
   ```
8. **Access Prometheus Web UI**:
   - Open your browser and go to: `http://<minikube-ip>:<NodePort>`
   ```sh
   minikube service prometheus-server-ext --url
   ```

---

## 2. Install Grafana

### Using Docker
To install Grafana using Docker, follow these steps:

1. **Pull the Grafana Docker image**:
   ```sh
   docker pull grafana/grafana
   ```
2. **Run the Grafana container**:
   ```sh
   docker run -d --name=grafana -p 3000:3000 grafana/grafana
   ```
3. **Verify that the container is running**:
   ```sh
   docker ps
   ```
4. **Access Grafana Web UI**:
   - Open your browser and go to: `http://localhost:3000`
   - Default credentials:
     - Username: `admin`
     - Password: `admin`

### Using Helm
To install Grafana using Helm, follow these steps:

1. **Add the Grafana Helm repository**:
   ```sh
   helm repo add grafana https://grafana.github.io/helm-charts
   ```
2. **Update Helm repositories**:
   ```sh
   helm repo update
   ```
3. **Install Grafana using Helm**:
   ```sh
   helm install grafana grafana/grafana
   ```
4. **Check the running services**:
   ```sh
   kubectl get svc
   ```
5. **Expose Grafana service**:
   ```sh
   kubectl expose service grafana --type=NodePort --target-port=3000 --name=grafana-server-ext
   ```
6. **Retrieve service details**:
   ```sh
   kubectl get svc grafana-server-ext -n default
   ```
7. **Get Minikube IP**:
   ```sh
   minikube ip
   ```
8. **Access Grafana Web UI**:
   - Open your browser and go to: `http://<minikube-ip>:<NodePort>`
   ```sh
   minikube service grafana-server-ext --url
   ```

---

## 3. Install Kubernetes Tools (kubectl & Minikube)

### Install `kubectl`
1. **Download and install `kubectl`**:
   ```sh
   curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
   chmod +x kubectl
   sudo mv kubectl /usr/local/bin/
   ```
2. **Verify installation**:
   ```sh
   kubectl version --client
   ```

### Install Minikube
1. **Download Minikube**:
   ```sh
   curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
   ```
2. **Install Minikube**:
   ```sh
   sudo install minikube-linux-amd64 /usr/local/bin/minikube
   ```
3. **Start Minikube**:
   ```sh
   minikube start
   ```
4. **Verify installation**:
   ```sh
   minikube status
   ```

This guide helps you install and configure Prometheus and Grafana using both Docker and Helm, along with setting up Kubernetes tools like `kubectl` and Minikube.

