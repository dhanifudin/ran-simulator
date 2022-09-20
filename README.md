# Simulator

## Prerequisite

- Kubernetes Cluster (k3s for single machine)
- Helm version 3
- [kubetail](https://github.com/johanhaleby/kubetail) (Easy to monitor logs from multiple pods)

## Quick Installation

```
# Add helm repositories
helm repo add cord https://charts.opencord.org
helm repo add atomix https://charts.atomix.io
helm repo add onos https://charts.onosproject.org
helm repo add sdran https://sdrancharts.onosproject.org
helm repo update

# Install atomix and onos-operator in kube-system namespace
helm install atomix-controller atomix/atomix-controller -n kube-system --wait --version 0.6.9
helm install atomix-raft-storage atomix/atomix-raft-storage -n kube-system --wait --version 0.1.25
helm install onos-operator onos/onos-operator -n kube-system --wait --version 0.5.2

# Install sdran (not in kube-system namespace)
kubectl create namespace sdran
helm -n sdran install sdran sdran/sdran --version 1.4.5
```

## Install or Uninstall RAN Simulator

```
# Install simulator
helm -n sdran install ran-simulator .

# Uninsntall simulator
helm -n sdran uninstall ran-simulator
```

## How To Run Simulator

- Create model using yaml format or you can generate using Honeycomb Topo Generator tools
- Place your model into directory `files/model`
- Change value of pci.modelName into your new model name (without yaml extension).
- Install simulator into kubernetes using following command 
  ```
  helm -n sdran install ran-simulator .
  ```
- You can monitor the logs from pod using the following command
  ```
  kubetail -n sdran ran-simulator
  ```
- Other information can be gathered using onos-cli
  ```
  # Attach into onos-cli pod
  kubectl -n sdran exec -it $(kubectl -n sdran get pods -l type=cli -o name) -- /bin/sh
  # Please check (onos ransim get) help information
  onos ransim get nodes
  onos ransim get cells
  ```
