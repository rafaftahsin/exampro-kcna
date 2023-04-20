### Cluster

A logical grouping of all components within a cluster

### Namespace

A named logical grouping of kubernetes components within a cluster. Used to isolate different workloads on the same cluster 

### Node 

A virtual machine or underlaying server. There are two types of nodes: Control Plane and Worker nodes.

- Workers nodes is where your application or workloads run

- Control Plane nodes manage worker nodes

### Pod 

The smallest unit in k8s. It is an abstraction over a container. Generally defines an application workload

### Service 

A statip IP address and DNS name for a set of pods (persists an address even if a pod dies) and a load balancer 

### Ingress

Translates HTTP/S rules to point to services

### API Server 

The API Server allows usersto interact with k8s components using the kubectl or by sending HTTP requests.

 ### kubelet 

 kubelet is an agent installed on all nodes. kubelet allows users to interact with node via the API API Server and kubectl

 ### kubectl 

 A CLI that allows users to interact with the cluster and components via the API Server

 ### Cloud Controller Manager

 Allows you to link a cloud Service provider eg. AWS Azure GCP to levarage cloud services

 ### Controller Manager

 A control loop that watches the state of the cluster and will change the state back to desired state.

 ### Scheduler

 Determines where to place pods on nodes. Places them in a scheduling queue

 ### kubeproxy

 An application on worker nodes that provides routing and filtering rules for ingress (incoming) traffic to pods

 ### Network Policy

 Acts as a virtual firewall as the namespace level or pod-level

 ### ConfigMap

 allows you to decouple environment-specific configuration from your container image, so that your application are easily portable. Used to store non-confidential data in key-value pair.

 ### Secret
 small amount of sensitive data such as a password, a token or a key

 ### Volumes

 mounting storage eg. locally on the node, or remote to cloud storage

 ### Statefulset 

 provides guarantees about the ordering and uniqueness of these pods
 
 ### Replicaset

 Maintain a stable set of replica pods running ata given time. Can provide a guarantee of availability.

 ### Deployment

 is a blueprint for a pod (think Launch Template) deploys replica sets