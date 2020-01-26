# Devspace

```
minikube start
code .

cd hello-world
kubectl create ns devspace
kubectl ns devspace

devspace use namespace devspace
devspace deploy
kubectl get pods
devspace open  ## USE DOMAIN: hello-world.devspace.test

devspace dev ## OPEN SYNC MODE
# CHANGE A FILE AND RELOAD
```
