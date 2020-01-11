# This repo contain my learnings of kubernetes when playing with it.

### You can `exec` container within the pod

- exec to container when there is only one container in the pod

```bash
kubectl exec -it <pod_name> /bin/bash
```

- exec to container within pod when you have multiple containers in pod

```bash
kubectl exec -it <pod_name> -c <container_name> /bin/bash
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

- Return snapshot logs from pod nginx with multi containers

```bash
  kubectl logs nginx --all-containers=true
```

- Begin streaming the logs of the ruby container in pod web-1
 
```bash
 kubectl logs -f -c ruby web-1
```

- To streaming the logs from all containers in pods defined by label `app=nginx`

```bash
kubectl logs -f -lapp=nginx --all-containers=true
```

### To tell K8s about your `container` not pod `health` you write probes
- readinessProbe: 
     Periodic probe of container service readiness. Container will be removed
     from service endpoints if the probe fails. Cannot be updated. More info:
     https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes
  
- livenessProbe: 
     Periodic probe of container liveness. Container will be restarted if the
     probe fails. Cannot be updated. More info:
     https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-pro
bes 

### Three ways to define a probe
#### One and only one of the following should be specified when defining the `Probe`.

- httpGet
- exec
- tcpSocket 

### Security Context can be defined at pod level as well as container level. container inherit the security context of pod if not defined. If security context is defined at both level then container security context takes precedence.

##### Out of various feilds defined in the security context, below two at most common.

- runAsUser  <integer> : The UID to run the entrypoint of the container process. Defaults to user specified in image metadata if unspecified.
- runAsGroup <integer> : The GID to run the entrypoint of the container process. Uses runtime default if unset. 
  
### Label are defined under the metadata tag of a resource in k8s.

#### labels are Map of string keys and values that can be used to organize and categorize (scope and select) objects 

```bash
metadata:
  labels:
    name: my-lable
```
#### Use by match selectors of replication controllers and services. More info: http://kubernetes.io/docs/user-guide/labels
