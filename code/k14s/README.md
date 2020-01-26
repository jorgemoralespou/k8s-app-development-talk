### Step: Building and pushing container images to registry

This step can works against Minikube or remote cluster.

```bash
kubectl create ns k14s
kubectl ns k14s
docker login registry.test:5000 -u user -p password
```

## Step1 - Deploy application
```bash
kapp deploy -a hello-world -f step-1

kapp inspect -a hello-world --tree
kapp logs -f -a hello-world
```

## Step 2 - Deploy app with template processing
```bash
ytt -f step-2
ytt -f step-2 | kapp deploy -a hello-world -f- --diff-changes
ytt -f step-2 -v route="helloworld.k14s.test" | kapp deploy -a hello-world -f- --diff-changes
ytt -f step-2 -v route="helloworld.k14s.test" | kapp deploy -a hello-world -f- --diff-changes -y
```

## Overlays - Deploy with overlay processing
```bash
ytt -f step-2
ytt -f step-2 -f overlay | kapp deploy -a hello-world -f- --diff-changes
```

# Step 3 - Build image and replace img ref
```bash
ytt -f step-3 | kbld -f-
ytt -f step-3 | kbld -f- | kapp deploy -a hello-world -f- --diff-changes
```

# Step 4 - Build, push and replace img ref
```bash
ytt -f step-3 | kbld -f- | kapp deploy -a hello-world -f- --diff-changes
kapp inspect -a hello-world --raw --filter-kind Deployment | kbld inspect -f-
```

# Delete
```bash
kapp delete -a hello-world
```