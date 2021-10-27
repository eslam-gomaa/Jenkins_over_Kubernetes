# Jenkins_over_Kubernetes

K8s Yaml for deploying Jenkins over Kubernetes as a statefulset

---

**Note:** Change the storage class to yours --> `storageClassName: nfs-client`

## Steps

1. **Deploy Jenkins**

This deploys Jenkins in the `jenkins` namespace


```bash
kubectl apply -f jenkins.yml
```

---

2. **Create Ingress resource for Jenkins**

Modify it to match your needs & ingress controller

```
kubectl apply -f jenkins-ingress.yml
```


---

3. **Create Service account** to give Jenkins permissions on the build namespace.


```bash
kubectl apply -f sa-jenkins-build.yml
```

---

> **Optionally**

4. Create service account to give pods running in the build namespace permissions to create & manage resources in staging & prod namespaces

```bash
kubectl apply -f sa-build-staging-and-prod.yml
```


Thats it.