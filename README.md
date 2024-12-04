
## Install & Run on Ubuntu  

## 1. Minikube Installation 

**Note**: *Make sure docker is installed on your system if you are using docker, as minikube start won't work without docker driver.*

Refer to the docs for detailed steps - [@minikube/docs/start](https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download), [@minikube/docs/drivers/docker](https://minikube.sigs.k8s.io/docs/drivers/docker/)

```bash
Minikube is a tool to run Kubernetes locally.

    # Update the system
    sudo apt update

    # Download Minikube binary
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

    # Install Minikube binary
    sudo install minikube-linux-amd64 /usr/local/bin/minikube

    # Verify installation
    minikube version

    # Start the Minikube Kubernetes cluster
    minikube start

    # Check status
    minikube status
```

## 2. Kubectl Installation 

```bash
kubectl is the Kubernetes command-line tool.

    # Download kubectl binary
    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

    # Install kubectl
    sudo install kubectl /usr/local/bin/kubectl

    # Verify installation
    kubectl version --client
```

## 3. Helm Installation 

```bash
Helm is a Kubernetes package manager.

    # Download Helm installation script
    curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

    # Verify installation
    helm version
```
## 4. Create Helm Chart Package

```bash
    # make package
    helm package .
```

## 5. Deploy Helm Chart 

```bash
    # deploy helm chart
    helm install testapp ./cosmocloud-deploy-0.1.0.tgz --atomic --timeout 30s
    
    # verify deployment
    helm list

    # you can uninstall deployment by(if needed)
    helm uninstall testapp 
```

## 6. Checking the Status of Kubernetes Pods

```bash
    # List all pods(frontend, backend, redis) in the current namespace
    kubectl get pods
```

## 7. Accessing Kubernetes Services Locally via Port Forwarding

```bash
    # Access frontend on localhost:5175
    kubectl port-forward service/frontend-svc 5175:5173 

    # Access backend on localhost:8000
    kubectl port-forward service/backend-svc 8000:8000
```
