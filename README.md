# Dapr Dashboard

The Dapr Dashboard is a web-based UI for Dapr, allowing users to see information, view logs and more for the Dapr sidecars running either locally or in a Kubernetes cluster.

<p style="text-align:center">
  <img src="img/img.png">
</p>

## Getting started

### Local machine

First, make sure you have [Go](https://golang.org/dl/) installed.


```
git clone git@github.com:yaron2/dapr-ui.git
cd dapr-ui
go run main.go
```

Done! point your browser to http://localhost:8080.

### Kubernetes

1. Deploy the dashboard:

```
kubectl apply -f https://raw.githubusercontent.com/yaron2/dapr-ui/master/deploy/dashboard.yaml
```

Wait until the dashboard pod is in Running state:

```
kubectl get pod --selector=app=dapr-dashboard -w
```

2. Connect to the dashboard:

```
kubectl port-forward svc/dapr-dashboard 8080:8080
```

Done! point your browser to http://localhost:8080.

## Building from source

First, install the Angular CLI:

```
npm i @angular/cli
```

Build the website and the Go web server into the `/release` dir:

```
./buid.sh
```

### Building a Docker image

After you have the release dir in place, run:

```
docker build -t <image>:<tag> .
docker push <image>:<tag>
```