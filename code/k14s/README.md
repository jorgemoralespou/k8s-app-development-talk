### Step: Building and pushing container images to registry

This step can works against Minikube or remote cluster.

```bash
kubectl create ns k14s
kubectl ns k14s
```

## Step1
```bash
docker login registry.test:5000 -u user -p password
kapp deploy -a hello-world -f step-1
kapp deploy -a hello-world -f step-1 --diff-changes
kapp deploy -a hello-world -f step-1 --diff-changes -y

kapp inspect -a hello-world --tree
kapp logs -f -a hello-world
```

## Step 2
```bash
ytt -f step-2
ytt -f step-2 | kapp deploy -a hello-world -f- --diff-changes
ytt -f step-2 -v route="helloworld.k14s.test" | kapp deploy -a hello-world -f- --diff-changes
ytt -f step-2 -v route="helloworld.k14s.test" | kapp deploy -a hello-world -f- --diff-changes -y
```

## Overlays
```bash
ytt -f step-2
ytt -f step-2 | kapp deploy -a hello-world -f- --diff-changes
ytt -f step-2 -v route="helloworld.k14s.test" | kapp deploy -a hello-world -f- --diff-changes
ytt -f step-2 -v route="helloworld.k14s.test" | kapp deploy -a hello-world -f- --diff-changes -y
```

# Step 3
```bash
ytt -f step-3 | kbld -f-
ytt -f step-3 | kbld -f- | kapp deploy -a hello-world -f- --diff-changes
kapp inspect -a hello-world --raw --filter-kind Deployment
```

# Step 4
```bash
docker login registry.test:5000 -u user -p password

ytt -f step-3 | kbld -f- | kapp deploy -a hello-world -f- --diff-changes
kapp inspect -a hello-world --raw --filter-kind Deployment | kbld inspect -f-
```

# Delete
```bash
kapp delete -a hello-world
```