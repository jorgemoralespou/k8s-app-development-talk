# Helm


```
code .
minikube start

kubectl create ns helm
kubectl ns helm

helm install hello-world .
# OPEN IN BROWSER: http://hello-world.helm.test
helm uninstall hello-world
# Make a type (e.g. in deployment add a space to a param)
helm install hello-world ./hello-world
```
