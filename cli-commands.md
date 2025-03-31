# Minikube Setup and Kubernetes CRUD operations

## Installation

### Install Hyperkit and Minikube
Before setting up Minikube, ensure that Homebrew is updated and install the required dependencies.

```bash
brew update                             # Update Homebrew package manager
brew install docker                     # Install Docker for hypervisor
brew install minikube                   # Install Minikube (Kubernetes local cluster manager)
kubectl                                 # Verify kubectl installation
minikube                                # Verify Minikube installation
```

### Create a Minikube Cluster
Start a Minikube cluster using **Hyperkit** as the virtual machine driver.

```bash
minikube start --vm-driver=hyperkit     # Start Minikube with Hyperkit
kubectl get nodes                       # Check if the Kubernetes node is running
minikube status                         # Verify Minikube cluster status
kubectl version                         # Check the Kubernetes version
```

### Delete Cluster and Restart in Debug Mode
If needed, you can delete the cluster and restart it with detailed logging for debugging.

```bash
minikube delete                         # Delete the existing cluster
minikube start --vm-driver=hyperkit --v=7 --alsologtostderr # Restart in debug mode
minikube status                         # Check Minikube status
```

## Working with Kubernetes using kubectl

### Retrieve Information
Use these commands to retrieve information about various Kubernetes resources.

```bash
kubectl get nodes                       # List all nodes in the cluster
kubectl get pod                         # List of all running Pods
kubectl get services                    # List all services
kubectl get deployment                  # List all deployments
kubectl get replicaset                  # List ReplicaSets in the cluster
kubectl get namespace                   # List all namespaces in the cluster
kubectl get all                         # List all resources in the cluster
```

### Create Resources
Create deployments and services using `kubectl` commands.

```bash
kubectl create deployment nginx-depl --image=nginx
# Create an Nginx deployment
kubectl create deployment mongo-depl --image=mongo
# Create a MongoDB deployment
```

### Update Resources
Modify an existing deployment configuration.

```bash
kubectl edit deployment nginx-depl      # Edit the deployment configuration
```

### Debugging Kubernetes Pods
Use these commands to troubleshoot issues with running Pods.

```bash
kubectl logs {pod-name}                 # View logs of a specific Pod
kubectl exec -it {pod-name} -- bin/bash # Open an interactive terminal inside a Pod
kubectl describe pod mongo-depl-{pod-name}  # Get detailed information about a specific Pod
```

### Delete Resources
To remove deployments, use the following commands.

```bash
kubectl delete deployment mongo-depl    # Delete MongoDB deployment
kubectl delete deployment nginx-depl    # Delete Nginx deployment
```

### Manage Deployments Using Config Files
Create or modify deployment configurations using YAML files.

```bash
vim nginx-deployment.yaml               # Create or edit an Nginx deployment config file
kubectl create -f nginx-deployment.yaml # Create the resources in the cluster
kubectl apply -f nginx-deployment.yaml  # Apply the configuration to the cluster
```

### Delete Deployments Using Config Files
To delete a deployment created with a YAML file, use:

```bash
kubectl delete -f nginx-deployment.yaml # Delete deployment using the config file
```

### Monitor Cluster Metrics
Monitor resource usage of the cluster’s nodes and Pods.

```bash
kubectl top                             # View current CPU and memory usage of Pods or Nodes
