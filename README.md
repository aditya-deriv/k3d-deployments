# k3s-deployments (in local environment using k3d)
Repo for k3s workshop on deployments, rolling updates and rollbacks


# Important definitions

## What is a deployment/ rollout?
---
A Deployment (Rollout) provides declarative updates for Pods and ReplicaSets.

You describe a desired state in a Deployment, and the Deployment Controller changes the actual state to the desired state at a controlled rate. You can define Deployments to create new ReplicaSets, or to remove existing Deployments and adopt all their resources with new Deployments.


## What is a rolling update/ rollover? 
A rolling update is the default deployment strategy in kubernetes. It lets you update a set of pods with no downtime through incremental pod replacement with new instances that run a new version of the application.

## Are there any other Deployment startegies?
Yes: https://spot.io/resources/kubernetes-autoscaling/5-kubernetes-deployment-strategies-roll-out-like-the-pros/

## What is a rollback?


## What is a replicaset?

