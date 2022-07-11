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
kubectl describe node <nodename> | grep Taints
```
