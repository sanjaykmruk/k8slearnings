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
