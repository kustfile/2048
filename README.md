# 2048 kustomize templates

## Usage

### install

Make sure kubectl version is above v1.14.x

```
kubectl apply -k overlays/dev
```

or apply with other environments, test, prod, etc.


### Access

Run port-forward in one shell console

```
$ kubectl get all -n 2048-dev

$ kubectl port-forward service/dao-2048 8080:80
```

Go browser with url http://localhost:8080 to play the game.
