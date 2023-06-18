# KubeCTL

kubectl - api-server - k8scomponets

kubectl looks for a file named config in the $HOME/.kube/config or ~/.kube/config

kubectl [command] [type] [name] [flags]

[ command ]
annotation - keyvalue data that can be applied to resource.
apply - executes manifest files ... 
auth - instpects if user is authorized to perform a action
autoscale - creates an autoscaler that automatically scales the number of pods that runs in the cluster.
cp - copy files and directories from and to containers.
create - creates specific k8s cluster level resource: ConfigMap, Job, Deployment, Namespace, Role & Secret.
delete - delete resources filesnames, stdin, resources and names, or by resources and label select.
describe - show details of a specific resource or group of resources.
diff - diffs online configuration with local config
edit - edit resource from the default editor. Edit a deployed manifest file and apply the changes.
exec - execute a command within a conainer.
expose - expose a resource as k8s service
get - get status of k8s resource.
kustomize - print a set of API resources generated from instructions in kustomization.yaml file
label - update labels on a resource.
logs - prints logs of a container, pod or specific resoruce.
patch - update fileds of a resource using strategic merge patch, a JSON merge patch or a JSON patch
port-forward - Forward one or more local ports to a pod
proxy - creates a proxy server between localhost and kube API Server
run - creates and run a container image in a pod
scale - set a new size for a deployment, replicaset, replication controller or stateful set.

[TYPE]

type is the resource type you want to command

kubectl describe deployments


resources can have abbreviations
- deployment -> deploy
- persistentVolumes - pv
- pods - po

There are over 50+ resource types ... 

[ NAME]

names are case sensitive,
you can specify more than one name 

[FLAG]
--server, -s

available commands varies based on commands ... 

https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands



*** Need to check annotation vs label
*** What happens if I exec to a pod ... 
*** task - run a single pod and expose it ... 
*** to print log of container you write kubectl logs <pod> -c <container>, if you try to get log of a deployment it will print log of choosen pod from the deployment.

# KubeCTL Commands Ref Follow Along
