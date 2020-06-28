# Kubernetes Local Setup

{% tabs %}
{% tab title="1. Machine Setup" %}
**Disable Proxy & VPN**

```text
unset http_proxy
unset https_proxy
unset HTTP_PROXY
unset HTTPS_PROXY
unset no_proxy
```

**Machine Setup**

```bash
# Install Docker Desktop
https://www.docker.com/products/docker-desktop

# Enable Kubernetes
Docker Desktop >> Preferences >> Kuberentes >> 
    - Enable: Kubernetes
    - Enable: Deploy Docker Stacks to Kubernetes by default

# Wait until `Docker` & `Kubernetes` are Running

# Install `minikube`
brew install minikube 

# Start Minikube
# minikube start --vm=true

# Start Minikube (hyperkit) if we need Ingress
minikube start --driver=hyperkit

#  Enable Ingress in Minikube
minikube addons enable ingress 
# Check: Ingress is enabled
minikube addons list

# Check: `ingress-nginx*` listed
kubectl get pods -n kube-system
```
{% endtab %}

{% tab title="2. Sample App Setup " %}
**Sample App Setup**: **`sock-shop`** 

```bash
# Create NameSpace `sock-shop`
kubectl create namespace sock-shop

# set `sock-shop` namespace for the current context
# kubectl config set-context $(kubectl config current-context) --namespace=sock-shop 
kubectl config set-context --current --namespace=sock-shop

# Check namespace is set properly for the currentContext
kubectl config get-contexts

# Import `sock-shop` microservice application
git clone https://github.com/jagadeeshpalaniappan/sock-shop-traefik

# Goto: sock-shop-traefik
cd sock-shop-traefik

# Apply All Objects (using YAML configuration)
kubectl apply -f .

# List All Objects
kubectl get all -A

# List Services
kubectl get services

# Create 'NodePort' type Service 
kubectl expose --type=NodePort --name=front-end-nodeport deploy/front-end

# Get the URL: 
minikube service front-end-nodeport --url --namespace=sock-shop
http://192.168.64.4:31211 # example url

# Open in Browser
http://192.168.64.4:31211

# Happy Coding....!
```
{% endtab %}
{% endtabs %}



