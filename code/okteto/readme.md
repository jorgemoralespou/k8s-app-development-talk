# Okteto

```
minikube start
code .

cd hello-world
kubectl create ns okteto
kubectl ns okteto

kubectl apply -f k8s.yml
okteto up
# OPEN IN BROWSER: http://localhost:8080
# Make a change in main.go
# Reload browser
```
