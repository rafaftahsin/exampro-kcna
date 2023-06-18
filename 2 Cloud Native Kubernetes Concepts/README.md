# What is Cloud Native - https://www.youtube.com/watch?v=UyxeHUZ_3gI

# Cloud Native vs Cloud Service Provider - https://www.youtube.com/watch?v=vayqKXVG40s

# Cloud Native Shared Responsbility Model - https://www.youtube.com/watch?v=2jyqiIurGLM

# The Linux Foundation - https://www.youtube.com/watch?v=ObTSptn30JE

# Cloud Native Computing Foundation - https://www.youtube.com/watch?v=fD2l2GU05XQ

# Preview LF and CNCF Website Follow Along - https://www.youtube.com/watch?v=Y2DurDuwzMU

# Cloud Native Landscape - https://www.youtube.com/watch?v=vtZJdI8A3-k

# Cloud Native Landscape Follow Along - https://www.youtube.com/watch?v=J6ajX36DsaE

# Cloud Native Trail Map - https://www.youtube.com/watch?v=6Yxq9EE5nXc

# Cloud Native Trail Map Follow Along - https://www.youtube.com/watch?v=AF5VchosQbo

# VMs vs Containers - https://www.youtube.com/watch?v=118uUAkY79U

# Micro services - https://www.youtube.com/watch?v=7goGLxHuoSo

# Kubernetes - https://www.youtube.com/watch?v=DoDUtU4DS4Q

# Kubernetes Components - https://www.youtube.com/watch?v=hjVR9aDmEUg


    Kubernetes API Server
        - API Server allows users to interact with k8s components using the kubectl or by sending HTTP requests
    Ingress

    kubelet
        - an agent installed on all nodes. kubelet allows users to interact with node via the API server and kubectl


    what are the services that must run in worker nodes ?
    What are the services that must run in control plane ?

    Cloud Controller Manager
        - Allows you to link a Cloud Service Provider (CSP) e.g. AWS, Azure GCP to leverage cloud services.

    Controller Manager
        - A control loop that watches the state of the cluster and will change the current state back to desired state.

    Scheduler
        - determines where to place pods on nodes. Place them in a scheduling queue.

    kube proxy
        - An Application on worker nodes that provides routing and filtering rules for ingress (incoming) traffic to pods

    Network Policy
        - Acts as a virtual firewall as the namespace level or pod level

    configmap
        - allows you to decouple environment-specific configuration from your container images, so that your application are easily portable. Used to store non-confidential data in key-value pair.

    secret
        - small amount of sensitive data such as password, a token, or a key. | basically a configmap with an option to encrypt it. by default base64 decoded.

    volumes
        - mounting storage eg. locally on the node, or remote to cloud storage.


    stateful set
        - provides guarantees about the ordering and uniqeness of these pods
            - like databases where 
            - stateful sets are hard, when you can host your db exterally from k8s cluster.

    ReplicaSets
        - Maintain a stable set of replica pods running at a given time. Can provide a guarantee of availability

    Deployment
        - is a blueprint of a pod
        - a deployment deploys replicaset
        - a replicaset deploys pod


# Manifest Files in Kubernetes - https://www.youtube.com/watch?v=PzTaItw_g0Q

    can be written with json / yaml

    apiVersion: v1
    kind: Service
    metadata:
        name: my-nginx-svc
        lables:
            app: nginx
    spec:
        type: LoadBalancer
        ports:
        - port: 80
        selector:
            app: nginx

--- for multiple yaml in single menifest file

can be applied with `kubectl apply -f <manifest file>

# Control Plane and Worker Nodes - https://www.youtube.com/watch?v=46b5bi2cchA

Control Plane Node (Formally known as Master Node)
    - Scheduling
    - Restarting Nodes
Worker Nodes
    - Does the work, running app in pods and container


API Server: backbone in communication
Scheduler - Resides in master. determines where to start a pod on worker node 
Controller Manager: detect state changes (if pod crashes, it restarts it.) master node
etcd: A key value store that stores the state of the cluster. Master node.
kubelet: allowes user to interact with the node via kubectl. it's present in both master and slave node.
kube-system namespace | in master that included etcd, controlller manager, kubelet and etcd

There CoreDNS - service discovery resides in master 

Worker node has container runtime.
worker node has proxy [kubeproxy], 
worker node has iptables ... and container and pod runs here 


# Pods - https://www.youtube.com/watch?v=ytYrdeJdrz4

Pods are the smallest unit in kubernetes that wraps the container.
There can be multiple container in a pod

parsistent volume : 

Each pod gets its private IP address
containers can talk to each other via localhost
containers run on different port

each pod can have shared storage volume attached

when the last remaining container dies (maybe crashes) in a pod so does the pod

When a replacement pod is created it gets a new IP address. IP address are temporary, they can be persisted to a pod.

`kubectl get pod -o wide`


# API Server - https://www.youtube.com/watch?v=ZTDWXlyT_J0

The core of k8s control plane is the API Server. API server exposes HTTP API that lets end users, different parts of your cluster, and external components communicate with one another.

main implementation is kube-apiserver. kube-apiserver is designed to scale horizontally. that is it scales by deploying more instances. kube-apiserver can be run in several instances and can load balanced.


Everything has to go through the API server

Interacting with API server can be done by 3 ways

    - UI* [ confusing kubernetes dashboard doesn't do that much ]
    - API
    - CLI KubeCTL

# Deployment - https://www.youtube.com/watch?v=1c5KpmRTOvI

provides declarative updates for pods and replicasets

Default deployment controller can be swapped out for other deployment tools like ArgoCD, Flux, JenkinX

A deployment always deploys replica set. even it is one pod, it deploys replicaset with replica one. replica set deploys pod

# Replica Sets - https://www.youtube.com/watch?v=_Ir-mhHJm2U

is a way to maintain a desired amount of pods.

it's not recommended to directly create replica set without deployment.

*** Task: create a pod
    create a pod with replica set without deployment
    create a pod with replica set with deployment.

HPA can be used to autoscale a replicaset.

Why deployment when we have replicaset ? 

https://stackoverflow.com/questions/55437390/k8s-why-we-need-replicaset-when-we-have-deployments

https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/

# Stateless vs Stateful - https://www.youtube.com/watch?v=gOjicJn0iYE



# Stateful Sets - https://www.youtube.com/watch?v=goMUN3QObGc

Stateful Sets are used when you need traffic to be sent to a specific pods

Stateful set will always have
    - a unique and predictable name and address
    - ordinal index number assigned each pod
    - a persistent volume attached, with a persistent link from pod to that storage
        - if a pod is rescheduled the original persistent volume will be mounted to ensure data integrity and consistency.

Stateful set pods will always start with the same order and terminate in the reverse order.

Stateful sets require a ***'headless'*** who knows  service to manage the identities.



# Namespaces - https://www.youtube.com/watch?v=987eVGxyxY8

kubectl get namespace

defalut -> default namespace ... 

kube-public -> for resources that are publicly visible

kube-system -> k8s system resource

kube-node-lease -> used to detect node failures by sending heartbeat


3 Kinds of k8s object
    - Single Namespace Object - like ConfigMaps and Secrets
    - Multiple Namespace Objects - like service, pods
    - Cluster-Wide Objects - Volume and Nodes

# In Tree vs Out Tree - https://www.youtube.com/watch?v=zUlUUcSAn0I

In-Tree -> Plugins, components or functionality that are provided by default

Out-of-Tree -> External plugins etc 

# In Tree vs Out Free Follow Along - https://www.youtube.com/watch?v=otwQz0WfC_E

# Endpoints and Endpoint Slices - https://www.youtube.com/watch?v=qdbpKqYMRyY

Endpoint track the IP address of the pods assigned to a Kubernetes service.

kubectl get endpoints

Endpoint slices break up Endpoints into smaller managable segments. Each endpoint slice has limit of 100 pods

# Jobs and Cron Jobs - https://www.youtube.com/watch?v=cF7zcbGNrtg

kubectl run -> 

kubectl create job ... 

kubectl create cronjob hello --image=busybox --schedule= ... 

# Kubernetes Dashboard - https://www.youtube.com/watch?v=RtdxR7fDnSs

open source application 