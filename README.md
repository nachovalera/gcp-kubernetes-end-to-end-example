# GCP Kubernetes simple end-to-end example

First of all, create a GCP Kubernetes Engine cluster, and connect to the cluster

## Build image with Cloud Build

Change proyect-name with your GCP proyect in the commands and in deployment.yaml
Then execute the following commands

```bash
cd image
gcloud builds submit --tag gcr.io/proyect-name/kubernetes-end-to-end-example .
cd ..
```

## Apply into kubernetes

```bash
kubectl apply -f deployment.yaml
```

## Deploy LB

```bash
kubectl apply -f lb-service.yaml
```

## Get info and LB ip
```bash
kubectl describe service end-to-end-example-LB
```
Then check the ip in a browser. It should say 'Hello World'

## Delete pods and services
```bash
kubectl delete services end-to-end-example-lb
kubectl delete deployment end-to-end-example
```
