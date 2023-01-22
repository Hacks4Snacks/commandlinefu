## Get all cert-manager resources

```Shell
kubectl get Issuers,ClusterIssuers,Certificates,CertificateRequests,Orders,Challenges --all-namespaces
```

## Reset Kubeadm cluster

```Shell
kubeadm reset
```

## Get Kubernetes Node Taints

```Shell
kubectl describe node <nodename> | grep -i taints
```

## Portforwarding from Kubernetes to localhost

```Shell
kubectl port-forward -n <namespace> <service> <localport>:<remoteport>
kubectl port-forward -n monitoring svc/lma-kube-prometheus-stack-prometheus 8080:9090
```

## Get Namespace, Pod, and in-use Container Images Mapped Together

```Shell
kubectl get pods --all-namespaces -o json | jq -r '.items[] | select(.status.phase == "Running") | .metadata.namespace + " " + .metadata.name + " " + .spec.containers[].image'
```