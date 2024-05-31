# Installation

This article describes about installation steps for belo tools

- Docker
- Kubectl CLI
- Minikube Kubernetes
- HELM chart for Kubernetes

### Docker Installation

Uninstall old versions

```bash
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

Set up Docker's apt repository

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

Install the Docker packages

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

Verify Docker version

```bash
docker --version
```
Docker is installed successfully.

### kubectl CLI Installation

Download the latest release

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

Install kubectl

```bash
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

Verify kubectl version

```bash
kubectl version --client
```

Minikube Kubernetes Installation

Download binary

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikube-linux-amd64
```

Install Minikube

```bash
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

Verify minikube version

```bash
minikube version
```

### HELM Kubernetes Installation

Download your [desired version](https://github.com/helm/helm/releases)

Unpack it 

```bash
tar -zxvf helm-v3.0.0-linux-amd64.tar.gz
```

Find the helm binary in the unpacked directory, and move it to its desired destination

```bash
mv linux-amd64/helm /usr/local/bin/helm
```

Verify HELM help command

```bash
helm help
```

### Reference Links

 - [Docker](https://docs.docker.com/engine/install/ubuntu/)

 - [Kubectl CLI](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)

 - [HELM Kubernetes](https://helm.sh/docs/intro/install/)
