# Installation on Azure CLI

[Azure Cli](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)

**Configure Azure CLI**

```
# -n Name of Cluster
# -g Resource Group
az aks get-credentials -n mwa -g mwa -f -

export KUBECONFIG=~/.kube/config-aks

# Get cluster info
kubectl cluister-info
```

Start the application

```
kubectl apply -f kube.yml
```

Check for deployment status

```
kubectl describe pvc mongovol1

kubectl describe persistentvolume pvc-xxxxxx-yyyy-zz

kubectl get pods

kubectl exec mongo1-xxxxx -- mongo --eval 'rs.initiate( {
    _id : "rs0",
    members: [
        { _id: 0, host: "mongo1:xxxx" },
        { _id: 1, host: "mongo2:xxxx" },
        { _id: 2, host: "mongo3:xxxx" }
    ]
})'

kubectl get service

kubectl scale --replicas=3 deployment api
```

**Removal**
kubectl delete -f kube.yml