<!-- classes: title -->

# O-RAN Simulation
## Using SD-RAN (onosproject)

<!-- block-start: grid -->
<!-- account: github, dhanifudin -->
Dian Hanifudin Subhi
<!-- block-end -->

---

<!-- section-title: Outline -->

## Outline

- Basic
- Installation
- Running Simulation
- Developing App

---

<!-- section-title: Basic of Docker -->

## Basic of Docker

Docker is an open platform for developing, shipping, and running applications.

---

## Docker Architecture

![Docker Architecture](https://docs.docker.com/engine/images/architecture.svg)
from https://docs.docker.com

---

## Docker Architecture (cont..)

- **Docker Daemon** (dockerd): daemon listens for Docker API requests and manages
  Docker objects.
- **Docker Client**: the primary way of users to interact with Docker.
- **Docker Desktop**: Application for Mac, Windows or Linux environment to make it easier
  to manage Docker and also Kubernetes.
- **Docker Registries**: registry to store Docker images. Example: Docker Hub
- **Docker Objects**: images, containers, networks, volumes, plugins and other
  objects.

---

## Virtualization vs Container

![VM vs Container](../images/container-vs-vm.png)

---

## Basic of Kubernetes

Kubernetes, also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications.

---

## Kubernetes Architecture

![Component of Kubernetes](../images/components-of-kubernetes.svg)

---

## Namespace

---

## Cluster

---

## Pod

---

## Basic of Helm

**Helm** is a package manager. Similar with package manager for other platforms like
**apt**, **yum** or **homebrew**. **Helm** helps you manage Kubernetes applications.

---

## Helm Chart

- Helm uses a packaging format called charts.
- Structure of helm chart

```bash
sd-ran
├── Chart.lock   # Lock file
├── Chart.yaml   # A YAML file containing information about the chart
├── README.md    # Optional: A human readable README file
├── charts/      # A directory containing any charts upon which this chart depends.
├── files/       # Additional files to support application
├── templates/   # A directory of templates that when combined with value,
|                # will generate valid Kubernetes manifest files.
└── values.yaml  # The default configuration value for this chart
```

[More Info](https://helm.sh/docs/topics/charts/)

---

## Helm Basic Command

```bash
# Add helm repositories
helm repo add name https://chart.url
# Update helm repositories
helm repo update
# Helm install
helm -n namespace install name repo-name/name-of-package
helm -n namespace install name location-chart-directory
# Helm uninstall
helm -n namespace uninstall name
```

---

## Basic of Go Language

- Go is an open source programming language supported by Google
- Easy to learn and get started with (less keyword, OOP without class)
- Built-in concurrency and a robust standard library (using goroutine and channel)

---

## Basic Structure of Go

```go
package main

import "fmt"

func main() {
	hello := Hello{language: "Korean"}
	hello.sayHello()
}

type Hello struct {
	language string
}

func (h Hello) sayHello() {
	if h.language == "Korean" {
		fmt.Println("Hello, 세계")
	} else {
		fmt.Println("Hello, World")
	}
}
```
<!-- fragments-start -->
```
Hello, 세계
```
<!-- fragments-end -->

---

## Basic of gRPC

gRPC is a modern open source high performance Remote Procedure Call (RPC).

---

## Basic of REST API

---

## Installation

---

## Installation
Prerequisites Installation

- **Docker**
- **Kubernetes** Cluster or **k3s**, **k3d**, **kind** or **microk8s** for single node
- **Helm** version 3
- Ubuntu 18.04/20.04 (Optional: SDRAN-in-a-Box method Installation)

---

## Installation
Add Helm Repositories

```bash
# Add repo cord, atomix and onos
helm repo add cord https://charts.opencord.org
helm repo add atomix https://charts.atomix.io
helm repo add onos https://charts.onosproject.org
# Optional or git clone sdran-helm-charts
# git clone https://github.com/onosproject/sdran-helm-charts
helm repo add sdran https://sdrancharts.onosproject.org
helm repo update
```

---

## Installation
Install components in kube-system namespace

```bash
helm install atomix-controller atomix/atomix-controller -n kube-system --wait --version 0.6.9
helm install atomix-raft-storage atomix/atomix-raft-storage -n kube-system --wait --version 0.1.25
helm install onos-operator onos/onos-operator -n kube-system --wait --version 0.5.2
```

---

## Installation
Prepare Kubernetes Namespace
```bash
# create sdran namespace
kubectl create namespace sdran
```

---

## Installation
Install sd-ran components

```bash
git clone https://github.com/onosproject/sdran-helm-charts
cd sdran-helm-charts

# helm -n namespace install release-name helm-charts-dir
helm -n sdran install sd-ran sd-ran
# or install without clone helm charts
helm -n sdran install sd-ran sdran/sd-ran
```

> If there are errors related with dependency, please run `helm dependency build sd-ran`
> then run helm install again.

---

## Installation

Monitor the installation of sd-ran components

```bash
kubectl -n sdran get pods

NAME                           READY   STATUS    RESTARTS   AGE
onos-a1t-5b6cdf4c7c-qg77s      2/2     Running   0          4m17s
onos-cli-89b47d4b7-npw6h       1/1     Running   0          4m17s
onos-config-76f8b49887-qt8lg   4/4     Running   0          4m17s
onos-consensus-store-0         1/1     Running   0          4m17s
onos-e2t-57ccb4b454-wb5gn      3/3     Running   0          4m17s
onos-topo-d66795968-qp6p4      3/3     Running   0          4m17s
onos-uenib-67d864bc76-55h2l    3/3     Running   0          4m17s
```

> **Tips**:
> We can combine command with `watch` to update output periodically
> `watch kubectl -n sdran get pods`

---

## Installation

**TLDR;**

[https://bit.ly/install-ran-simulator](https://bit.ly/install-ran-simulator)

---

# Running Simulation

---

## Video Demo

[Video Demo](https://drive.google.com/file/d/1Rv4Jw19OWESdqR6aO9RLQirl9FlzsKNL/view)

---

# Developing App

---

Thank You
