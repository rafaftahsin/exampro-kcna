# Selectors - https://www.youtube.com/watch?v=a4XA3d0uCFU

Selectors are a way of selectig one or more kubernetes Objects.

3 

1. Label Selector

2. Field Selector metada, status

3. Node Selector

kubectl get pods --show-labes

kubectl label pods apache-web onwner=devops

# Recommend Labels - https://www.youtube.com/watch?v=SMjZKK9jfvQ

app.kubernetes.io

app.kubernetes.io/name
app.kubernetes.io/instance
app.kubernetes.io/version
app.kubernetes.io/component
app.kubernetes.io/part-of
app.kubernetes.io/managed-by
app.kubernetes.io/created-by

# Selecting Labels - https://www.youtube.com/watch?v=Q95Jk4Hf0mo

services and replicasets can target pods based on label selectors


kubectl get pods --selector env=development
kubectl get pods -l env=development


# Annotations - https://www.youtube.com/watch?v=N_BoYZnuI8I

kubernetes annotations allows you to attach arbitary non-identifying metadata to objects. Clients can and may require this annotation in order to work.

Example:

Ingress often use annotation to communicate with Ingress-Controller