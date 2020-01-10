# This repo contain my learnings of kubernetes when playing with it.

### You can `exec` to pod or container within the pod

- exec to pod

```bash
kubectl exec -it <pod_name> /bin/bash
```

- exec to container within pod

```bash
kubectl exec -it <pod_name> <container_name> /bin/bash
```

### To install curl using apt-get 

- exec to container

```bash
apt-get upgrade # upgrade the apt-get to latest version and to get apt-get repointed correctly.
apt-get update # it updates the package lists for upgrades
apt-get install curl -y # insatlls curl
```
### You can't change every parametere in your pod yaml file. there are only certain field which can be changed.

```bash
The Pod "command-pod" is invalid: spec: Forbidden: pod updates may not change fields other than `spec.containers[*].image`, `spec.initContainers[*].image`, `spec.activeDeadlineSeconds` or `spec.tolerations` (only additions to existing tolerations)
```

### `Kubectl logs` give lot of useful options to view the logs of the the containers inside the pod. Some useful option are:

# Return snapshot logs from pod nginx with multi containers

``bash
  kubectl logs nginx --all-containers=true
```

 # Begin streaming the logs of the ruby container in pod web-1
 
 ```bash
 kubectl logs -f -c ruby web-1
 ```
 # To streaming the logs from all containers in pods defined by label `app=nginx`
```bash
kubectl logs -f -lapp=nginx --all-containers=true
```
