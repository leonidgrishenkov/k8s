```sh
docker buildx use container-builder
```

```sh
docker build -t ubuntu-nginx:latest --platform linux/amd64,linux/arm64 -f Dockerfile .
```

```sh
export YC_REGISTRY_ID=crpmqmh4rb0o34dn69to
```

```sh
docker tag ubuntu-nginx:latest cr.yandex/$YC_REGISTRY_ID/ubuntu-nginx:latest
```

Authenticate in cloud registry:

```sh
yc config profile activate personal-container-registry-admin
```

```sh
export YC_IAM_TOKEN=$(yc iam create-token)
```

```sh
echo $YC_IAM_TOKEN | docker login --username iam --password-stdin cr.yandex
```

```sh
docker push cr.yandex/$YC_REGISTRY_ID/ubuntu-nginx:latest
```

List images in cloud registry:

```sh
yc container image list --registry-id $YC_REGISTRY_ID
```

# k8s

```sh
export KUBECONFIG=~/.kube/config.yaml
```

## deployment

```sh
k get pods
```

```sh
k apply -f nginx-deployment.yaml
```

```sh
k get deployments
```

```sh
k describe deployment/nginx-deployment
```

```sh
k scale --replicas=3 deployment/nginx-deployment
```

```sh
k get pods
```

```sh
k delete deployment/nginx-deployment
```

## load balancer

```sh
k apply -f load-balancer.yaml
```

Get external IP address of load balancer:

```sh
k get services
```
