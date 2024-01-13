Kubernetes:
===========
O Kubernetes possui 2 componentes principais:
    - Control-Plane
    - Worker


Comandos:
=========

// Nodes and Namespaces:
kubectl get nodes
kubectl get namespaces

// Events
kubectl get events // all events
kubectl get events  --field-selector involvedObject.name=[pod-name] // specific pod

// Pods
kubectl get pods //default namespace
kubectl get pods -A -o wide
kubectl get pods -n [namespace]
kubectl describe pods [pod-name]
kubectl logs -f [pod-name]
kubectl exec -it [pod-name] -- bash // interact inside pod (container):
kubectl run nginx --image nginx // create pod with define image (running container)

// Deployment: 
kubectl get deployments
kubectl create deployment nginx --image nginx --port=80

// Service:
kubectl expose deployment/nginx --type="NodePort" --port 80 // service types: NodePort, ClusterIP, LoadBalancer

// Port-Forward:
kubectl port-forward service/nginx 8090:80 // To access in your machine

// Scale deployment
kubectl scale deployment [deploy-name] --replicas [num-replicas]

// Generate yaml (--dry-run=client -o yaml)
Example: 
    kubectl create deployment [deploy-name] --image nginx --port [port] --replicas [num-replicas] --dry-run=client -o yaml > deployment.yaml

Pod:
====
    - A menor unidade dentro do kubernetes é o pod.
    - É possível ter 1 ou mais containers dentro de um mesmo pod. 
    - É possível ter um sidecar, um proxy por exemplo ao lado da aplicação no mesmo pod.
    - Você nunca vai ter dois containers de aplicação no mesmo pod (Exemplo: Aplicativo Java + Banco de dados)
    
Deployment:
===========
    - O deployment me possibilita ter uma ou mais réplicas do meu serviço.
    - Tenho muito mais recursos para trabalhar com alta disponibilidade.

Kubernetes Gerenciado: 
======================
    * Significa que a parte de control-plane é gerenciado pelo provedor de nuvem

Exemplos:
    - EKS = Elastic Kubernetes Service (AWS)
    - AKS = Azure Kubernetes Service (Microsoft Azure)
    - GKE = Google Kubernetes Engine (Google)

--------------------------------- Links ---------------------------------

Using a service to expose your app: 
https://kubernetes.io/docs/tutorials/kubernetes-basics/expose/expose-intro/

Create deployment:
https://kubernetes.io/docs/tutorials/kubernetes-basics/deploy-app/deploy-intro/

Running your first container:
https://jamesdefabia.github.io/docs/user-guide/simple-nginx/

Run nginx on kubernetes: (Tutorial)
https://nonanom.medium.com/run-nginx-on-kubernetes-ee6ea937bc99

