Argo CD test CI/CD pipeline setup to give a demo of the flow of it's setup.

Install Argocd CLI (something like kubectl to interact with argo in a cluster) in local machine https://spacelift.io/blog/argocd#:~:text=deploying%20your%20app.-,Get%20the%20Argo%20CLI,-Argo%E2%80%99s%20CLI%20lets

To set up an ArgoCD proof of concept (POC) for its use as a release pipeline, you can follow these steps:

1. Install ArgoCD: You can install ArgoCD by following the installation guide from the official documentation. You can install it either on your local machine or on a Kubernetes cluster.
2. Create a Git repository: Create a Git repository to store your application manifests. You can use GitHub, GitLab, or any other Git hosting service of your choice.
3. Add your application manifests to the Git repository: Add your application manifests to the Git repository. You can create separate directories for different environments, such as development, staging, and production.
4. Create an ArgoCD application: Create an ArgoCD application by defining the source and destination of your application manifests. The source is the Git repository where your application manifests are stored, and the destination is the Kubernetes cluster where you want to deploy your application.
5. Configure the ArgoCD application: Configure the ArgoCD application by defining the sync policy, which specifies how often ArgoCD should check for updates and synchronise the application with the Kubernetes cluster. You can also define the rollback policy, which specifies how to rollback to a previous version of the application if needed.
6. Deploy the ArgoCD application: Deploy the ArgoCD application by clicking on the "Sync" button in the ArgoCD UI or by using the CLI.
7. Monitor the ArgoCD application: Monitor the ArgoCD application to ensure that it is deployed successfully and running as expected. You can use the ArgoCD UI or CLI to view the application status, logs, and metrics.

By following these steps, you can set up an ArgoCD POC for its use as a release pipeline. Once you have validated the POC, you can integrate ArgoCD into your software development lifecycle (SDLC) to automate the deployment of your applications to different environments.

### ARGO CD concepts:
A pull based CI/CD implementation

Argo controller- component installed in the cluster, implements kubernetes controller pattern to monitor application and compare state against repos.

Application - Group of k8s resources to collectively deploy workload as per the CRD specifications

Live State - Current state of application in Cluster

Target State - Version of state that is declared in your git repo, dictates the desired state there

Refresh - occurs when argo fetches desired/target state from git repo, argo will apply actions to bring cluster to desired target state

Sync - Process of applying the changes between target and live state to the k8s cluster.

```
$ wget https://github.com/argoproj/argo-cd/releases/download/v2.6.1/argocd-linux-amd64
$ chmod +x argocd-linux-amd64
$ mv argocd-linux-amd64 /usr/bin/argocd
```


Login to the dashboard of argoCD using localhost:8080 in web browser
The argocd cli can be accessed via the following command in terminal:
argocd login localhost:8080
- Input the same username and password that you would use for the web login.

If the environment is restarted (i.e computer/vm restarted or docker container restarted), Use these steps to get it back running.
run this command in the terminal:

`kubectl port-forward svc/argocd-server -n argocd 8080:443`  

and try to access `localhost:8080` to see if the login console for argocd shows up.


### Applications can be created by 2 methods :

1. using the CLI make sure to login to argocd using the argocd login `localhost:8080` command
`argocd app create guestbook --repo https://github.com/argoproj/argocd-example-apps.git --path guestbook --dest-server https://kubernetes.default.svc --dest-namespace default`  
2. Using the UI to add a new app by the + new app button.
   

### Sync commands can be also performed through both CLI and GUI:

1. list out all the contents of the application using the argocd app get <application-name> command.
2. Perform sync using the  argocd app sync <application-name> command


