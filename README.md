# k8s-tool
k8s tool for cka，including shell scripts and yaml files.

# generate yaml
```
# pod
kubectl run vk-pod --image=nginx --generator=run-pod/v1 --dry-run -o yaml

# deployment
kubectl create deployment vk-deploy --image=nginx --dry-run -o yaml

# service
kubectl create service clusterip vk-svc --tcp="5678:8080" --dry-run -o yaml 

# configmap
kubectl create configmap special-config --from-literal=special.how=very --from-literal=special.type=charm

# secret
kubectl create secret generic db-user-pass --from-literal=username=voidking --from-literal=password='vkpassword'
```

# expose service
```
kubectl expose deployment deployment-name --port=6789 --target-port=80
```

# csr
```
openssl genrsa -out voidking.key 2048
openssl req -new -key voidking.key -subj  "/CN=voidking" -out voidking.csr
cat voidking.csr | base64

kubectl apply -f voidking-csr.yaml
kubectl get csr 
kubectl certificate approve voidking
kubectl get csr voidking -o yaml
```