# learn-argo-cd

## Setup Argo CD locally

* Need to have a K8s locally
* Create a namespace for Argo CD - `kubectl create ns argocd`
* Non HA setup - `kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`
* Wait for pods to be running - `kubectl get pods -n argocd`
* Get initial admin password - `kubectl get secret -n argocd argocd-initial-admin-secret -o yaml`
* Decode from base64 - `echo -n “<pass>”  | base64`

## Accessing ArgoCD Server

* Port-forward - `kubectl port-forward svc/argocd-server -n argocd 8080:443`

* Open browser -  `https://localhost:8080/`

* Credential - `admin/<what-you-got-from-setup-step>`

## Setup Argo CD CLI

```
brew install argocd
```
 or follow official docs - https://argo-cd.readthedocs.io/en/stable/cli_installation/


### Login to Argo CD CLI

```
argocd login localhost:8080 --insecure --username admin --password <what-you-got-from-setup-step>
```

To check see clusters - `argocd cluster list`



