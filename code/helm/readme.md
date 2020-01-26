# Helm


```
cd hello-world

kubectl create ns helm
kubectl ns helm

helm install hello-world .
kubectl get pods

# OPEN IN BROWSER: http://hello-world.helm.test
helm uninstall hello-world

helm install hello-world . --set replicaCount=2

kubectl get pods

helm uninstall hello-world

# Make a type (e.g. in deployment add a space to a param)
helm install hello-world ./hello-world
```
