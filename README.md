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
