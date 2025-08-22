# Readme

## Quick Start Kubernetes (book)

Node.js web app for use with [Quick Start Kubernetes](https://leanpub.com/quickstartkubernetes) book.

Packages and dependencies will be updated annually. May contain vulnerable code, **use at own risk**.

## App

The app, dependencies, and Dockerfile are in the `/App` folder.

## Kubernetes YAML files

Simple YAML files are in the root folder.

## Additional references

List of additional books, courses, blogs, and other places this repo is used/referenced:

- None

## Pre-created image

Publicly available pre-created container images are available for download [here](https://hub.docker.com/r/nigelpoulton/qsk-book)

## Connect with me

I'm passionate about tech, and I'm all about making Kubernetes less scary!

- Twitter: [@nigelpoulton](https://twitter.com/nigelpoulton)
- LinkedIn: [Nigel Poulton](https://www.linkedin.com/in/nigelpoulton/)


## 使用k3d创建k3s集群

k3d cluster create mycluster --servers 1 --agents 2 --port 31111:31111@loadbalancer

kubectl apply -f pod.yml

kubectl apply -f svc-local.yml

创建集群时，将service的31111端口映射到了宿主机的31111端口，可直接访问127.0.0.1:31111。（你访问31111时，service会转发到pods的8080端口）

如果创建集群时没有指定端口映射，那么可以临时指定把宿主机的8080端口转发到pod的8080端口。kubectl port-forward pod/first-pod 8080:8080

或者转发到service的31111端口。kubectl port-forward svc/svc-local 8080:8080