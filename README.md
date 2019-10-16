# 2048 kustomize templates

## Usage

### install

Make sure kubectl version is above v1.14.x

```
kubectl apply -k overlays/dev
```

or apply with other environments, test, prod, etc.


### Access

Run port-forward

```
$ kubectl get all -n 2048-dev

$ kubectl port-forward service/dao-2048 8080:80
```

Go browser with url http://localhost:8080 to play the game.

### Diff between environments

```
$ diff <(kustomize build overlays/dev) <(kustomize build overlays/test)
5,6c5,6
<     name: 2048-dev
<   name: 2048-dev
---
>     name: 2048-test
>   name: 2048-test
16c16
<   namespace: 2048-dev
---
>   namespace: 2048-test
37c37
<   namespace: 2048-dev
---
>   namespace: 2048-test
58c58,64
<         resources: {}
---
>         resources:
>           limits:
>             cpu: 100m
>             memory: 100Mi
>           requests:
>             cpu: 100m
>             memory: 100Mi
```
