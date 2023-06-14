# PodSpecFile - https://www.youtube.com/watch?v=swCKx3iSJtg

PodSpec is a configuration file that describes a pod

```kubernetes
apiVersion: v1
kind: Pod
metadata:
    name: nginx
spec:
    container:
    - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort:80

```

The `spec` section will define
- multiple containers
- the name of the container
- image
- command to start up 
- port mapping
- restart policy

liveliness prob ??? 

You don't directly deploy pods ... instead you deploy deployments or job ... 

# gRPC - https://www.youtube.com/watch?v=riNzEelKO1s

RPC - Remote Procedure Call

RPC is a framework of communication in distributed systems. It allows one program on machine to communicate to communication with another program on remote machine without knowing it's remote. The concept of RPC has been around since 1970.

gRPC - modern open source high performance RPC, initially created by Google.

You can think gRPC as an alternative method of communication instead of REST or GraphQL.

gRPC can connect services in and across data centers with pluggable support for

- load balancing
- tracing
- health checking
- authentication

Kubernetes user gRPC for pod communication.

# Kubelet - https://www.youtube.com/watch?v=fiRRu9pQZ-I

kubelet is responsible for pod internal API communication via the API Server

kubelet is a node agent that runs on every single node (control plane and workers)

kubelet perform the following tasks:

- watches for pod changes
- configure the container runtime to 
    - pull images
    - create namespace
    - run containers

kubelet uses podspec files to determine what images to pull and container to run.


CRI - Cloud Runtime Interface
CSI - Cloud Storage Interface
CNI - Cloud Networking Interface