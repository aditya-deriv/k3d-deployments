# Workshop steps

## Deploying an application:
1) Create your deployment yaml file (already created for you in nginx-deployment.yaml file)
2) Apply your deployment using ```kubectl apply -f https://k8s.io/examples/controllers/nginx-deployment.yaml``` or ```kubectl apply -f <path/to/your/deployment.yaml/file>```
3) Run `kubectl get deployments` to verify status of the deployment creation.
4) It should show 3/3 in `Ready` row to confirm all replicasets are up.
5) Run `kubectl rollout status deployment/nginx-deployment` to see the current status of the rollout for the deployment. you can use `-w` flag to watch the status.
   - Run `kubectl get rs` to see the status of the replicaset specifically.
   - Run `kubectl get pods --show-labels` to view the auto assigned labels for each pod.

## Rolling release strategy:
By default, Rolling deployment is the default deployment strategy in kubernetes. It replaces the existing version of the pods with the new version slowly one by one, without cluster downtime.

## Example of rolling out changes to your deployment after it's already up and runnning:
1) Use a text editor to update your `nginx-deployment.yaml` file and change the spec.replicas value from `3` to `2`. (kubectl set command can also be used to perform this action although it is less recommended for enterprise use cases)
2) Apply the above deployment file by running `kubectl apply path/to/nginx-deployment.yaml` and check status of the rollout to all replicas with kubectl rollout status `kubectl rollout status deployment/nginx-deployment`
   -    A rollout can be paused midway (especially for larger deployments) manually by `kubectl rollout pause deployment/nginx-deployment`


## Rolling Back a deployment:

1) List all revisions of  a deployment by running `kubectl rollout history deployment/nginx-deployment`
2) To get a breakdown of a particular revision run `kubectl rollout history deployment/nginx-deployment --revision=<revision number>`
3) There are two ways to roll back
   - Directly to the last deployment by `kubectl rollout undo deployment/nginx-deployment`
   - To a specific revision by defining it using `kubectl rollout undo deployment/nginx-deployment --to-revision=<revision number>`
4) Once rollback is completed, you should be able to see the following output or something similar:
   - `deployment.apps/nginx-deployment rolled back`

