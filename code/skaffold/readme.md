# Skaffold


```
minikube start
code .

cd hello-world
kubectl create ns skaffold
kubectl ns skaffold

skaffold dev --port-forward
# OPEN IN BROWSER: http://localhost:8080
# Make a change in main.go
# Reload browser
```
