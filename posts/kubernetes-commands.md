---
layout: post
title: "Kubernetes Commands"
date: 2020-08-26
---

```shell
# Update aws-auth ConfigMap
kubectl edit configmap aws-auth -n kube-system
```

```yaml 
# Add the user/role
data:
    mapUsers: |
      - userarn: arn:aws:iam::XXXXXXXXXXXX:user/testUser
        username: testUser
        groups:
          - system:masters
    mapRoles: |
      - rolearn: arn:aws:iam::XXXXXXXXXXXX:role/testRole
        username: testRole
        groups:
          - system:masters
```

```shell
# Update the KubeConfig
aws eks --region us-east-1 update-kubeconfig --name 
```

```shell
# List
kubectl get pods
kubectl get svc
kubectl get deployments
kubectl get pod --show-labels
kubectl get pod -L env # List the label "env"
kubectl get nodes --show-labels

# List the pods with label matching the value or with a label
kubectl get pod -l creation_method=manual
kubectl get pod -l env
kubectl get ns
kubectl get pods --namespace kube-system
kubectl get rc
kubectl get rs
kubectl get ds
kubectl get jobs
kubectl get cronjobs

# Describe
kubectl describe pod ping
kubectl describe rc ping
```

```shell
# Creates
kubectl create -f ping-manual-with-labels.yaml
eksctl create cluster -f eksworkshop.yaml
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

```yaml
---
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: workshop
  region: us-east-1
  version: "1.17"

availabilityZones: ["us-east-1a", "us-east-1b", "us-east-1c"]

managedNodeGroups:
- name: t-nodegroup
  instanceType: t2.micro
  minSize: 1
  desiredCapacity: 1
  maxSize: 3
  ssh:
    allow: true
    publicKeyName: WorkshopAdmin

# To enable all of the control plane logs, uncomment below:
cloudWatch:
  clusterLogging:
    enableTypes: ["*"]

secretsEncryption:
  keyARN: arn:aws:kms:us-east-1:123456789012:key/123a456b-c7d8-9e1f-0g11-1h2i1k314151
```

```shell
# Updates
kubectl label pod ping-manual creation_method=manual # Add label to a POD
kubectl label node ip-123-456-78-9.us-east-2.compute.internal type=m5.large # Adding label to the node
kubectl annotate pod ping-manual smuralee.com/learning_k8=true # Adding annotation

# You need to use the --overwrite option when changing existing labels
kubectl label po ping-manual-v2 env=debug --overwrite
kubectl set image deployment/ping ping=smuralee/ping:1 # container_name=image_name
```

```shell
# Deletes
kubectl delete pod ping
kubectl delete pods --all
kubectl delete -f deployment.yaml
kubectl delete po -l creation_method=manual
kubectl delete ns custom-namespace
kubectl delete all --all
kubectl delete rc ping --cascade=false # Does not delete the pods, only RC
eksctl delete cluster --name=workshop
```

```shell
# IAM details
kubectl describe configmap -n kube-system aws-auth
curl -o aws-auth-cm.yaml https://amazon-eks.s3-us-west-2.amazonaws.com/cloudformation/2019-11-15/aws-auth-cm.yaml

# Kubenetes dashboard
kubectl proxy
# Access on browser: http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/
aws eks get-token --cluster-name workshop | jq -r '.status.token'

# Port forward to access the pod without service
kubectl port-forward ping-manual 9090:8080

# Logging
kubectl logs -f ping-manual

## Control plane logging
aws eks --region us-east-1 update-cluster-config --name workshop --logging '{"clusterLogging":[{"types":["api","audit","authenticator","controllerManager","scheduler"],"enabled":true}]}'
aws eks describe-update --name workshop --update-id a1bc2345-6789-101d-1e1f-2ghij131k4lm

## Refer the metrics server and auto-scaler
## Install prometheus for logs visualization
brew install helm
helm repo add eks https://aws.github.io/eks-charts
helm repo add stable https://kubernetes-charts.storage.googleapis.com
helm repo update

# Exec into the POD (-- is to ignore the -s, anything after -- is executed in the pod)
kubectl exec kubia-manual -- curl -s http://192.0.2.0
```


