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



---

## Basic of gRPC

---

## Basic of REST API

---

## Installation

---

# Running Simulation

---

# Developing App

---

Thank You
