# DevOps Exercise 2
This repository contains the yaml files for the second exercise

## Table of contents

* [Project information](#project-information)
* [Autoscaling](#autoscaling)

## Project information
This repository contains all yaml files necessary for the second exercise.  
* deployment.yaml
* service.yaml
* hpa.yaml  

For this project minikube and its dashboard was used.  
apply the yaml files with `kubectl apply -f *.yaml`  
![Dashboard](/screenshots/dashboard.png?raw=true "Minikube Dashboard")

## Autoscaling

To test the autoscaling a pod with BusyBox was deployed, which sends requests to the deployment.  
`kubectl run -i --tty load-generator --rm --image=busybox:1.28 --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://web-blog; done"
`  
![busyBox](/screenshots/busyBox.png?raw=true "BusyBox")
![busyBoxActive](/screenshots/busyBoxActive.png?raw=true "BusyBox Active")
And to check how the autoscaler increases the pods enter `kubectl get hpa -w`  
![get hpa](/screenshots/get-hpa.png?raw=true "Get HPA")


