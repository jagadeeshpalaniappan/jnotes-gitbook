# Kubernetes Commands

{% tabs %}
{% tab title="Context" %}
```bash

# list: all contexts 
kubectl config get-contexts     

# display: current selected context 
kubectl config current-context

# set: default context
kubectl config use-context my-cluster-name

# permanently save the namespace for all subsequent kubectl commands in that context.

# set: default namespce -for current-context
kubectl config set-context --current --namespace=sock-shop
# or
kubectl config set-context $(kubectl config current-context) --namespace=sock-shop 

```
{% endtab %}

{% tab title="Get: Objects" %}
```bash

# list: all objects
kubectl get all -A

### Namespaces
kubectl get ns
kubectl get ns - o yaml
kubectl describe ns


### Nodes
kubectl get nodes # list: all nodes
kubectl get no # shortcut
kubectl get noodes -o=wide # list: all nodes (with more info)
kubectl get nodes -o=yaml # list: all pods (with yaml info)
kubectl describe nodes # list: all nodes details


### Pods
kubectl get pods # list: all pods
kubectl get po # shortcut
kubectl get pods --show-labels # list: all pods with labels
kubectl get pods -o=wide # list: all pods (with more info)
kubectl get pods -o=yaml # list: all pods (with yaml info)
kubectl get pod [pod_name]
kubectl get pod [pod_name] -o=yaml --export > pod.yaml


### Services
kubectl get services
kubectl get svc
kubectl describe svc
kubectl get svc -o=wide
kubectl get svc -o=yaml
kubectl get svc --show-labels



### Deployments
kubectl get deployments
kubectl get deploy # shortcut
kubectl get deployment [dep_name]
kubectl get deployments -o=wide
kubectl get deployments -o=yaml


### ReplicaSets
kubectl get replicasets
kubectl get rs # shortcut
kubectl get rs [dep_name]
kubectl get rs -o=wide
kubectl get rs -o=yaml

```
{% endtab %}

{% tab title="Create: Object" %}
```bash
## Add any Resources
kubectl create -f [file_name]  # create any object
kubectl apply -f [file_name]   # create or update any object
kubectl apply -f . # apply: currentFolder

## Creating a Pod (using imperative cmd)
kubectl run [pod_name] --image=nginx --restart=Never
kubectl run [pod_name] --generator=run-pod/v1 --image=nginx
kubectl run [pod_name] --image=nginx --restart=Never

## Creating a Deployment (using imperative cmd)
kubectl create deploy [deploy_name] --image=nginx
kubectl create deploy [deploy_name] --image=nginx --dry-run -o=yaml > deploy.yaml # Output YAML to a File

## Creating a Service (using imperative cmd)
kubectl create svc nodeport [svc_name] --tcp=8080:80
```
{% endtab %}

{% tab title="Logs" %}
```bash
kubectl logs [pod_name]
kubectl logs --since=1h [pod_name]
kubectl logs --tail=20 [pod_name]
kubectl logs -f -c [container_name] [pod_name]
kubectl logs [pod_name] > pod.log
```
{% endtab %}
{% endtabs %}

