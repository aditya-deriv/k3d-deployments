# k3s-deployments (in local environment using k3d)
Repo for k3s workshop on deployments, rolling updates and rollbacks

# Prerequisites:
1) Have a version of kubernetes running locally (k3s, minikube, microk8s).
2) Ensure docker is installed.
4) Ensure kubectl is installed.
3) Ensure a cluster is created and available.

# Important definitions

## What is a deployment/ rollout?
A Deployment (Rollout) provides declarative updates for Pods and ReplicaSets.

You describe a desired state in a Deployment, and the Deployment Controller changes the actual state to the desired state at a controlled rate. You can define Deployments to create new ReplicaSets, or to remove existing Deployments and adopt all their resources with new Deployments.


## What is a rolling update/ rollover? 
A rolling update is the default deployment strategy in kubernetes. It lets you update a set of pods with no downtime through incremental pod replacement with new instances that run a new version of the application.

## Are there any other Deployment strategies?
Yes: https://spot.io/resources/kubernetes-autoscaling/5-kubernetes-deployment-strategies-roll-out-like-the-pros/

## What is a rollback?
It's the process of failing back on an older version of the deployment to recover from a failed deployment or an other reason such as a bug.

## What is a replicaset?
A replicaset is a process that runs multiple instances of a pod and keeps the specified number of Pods constant as defined in the yaml file.

## Labs and their contents:
- lab 1
	- Main focus is on Deployments, Rolling updates and rollback examples.
- lab 2 
	- Main focus is on Sidecars, Init pods, Config Maps and secrets. 

