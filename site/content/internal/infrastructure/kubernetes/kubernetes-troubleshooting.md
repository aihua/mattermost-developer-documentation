---
title: "Kubernetes Troubleshooting"
date: 2018-11-07T15:24:42+01:00
weight: 10
---

This page have the intent to help the developers access and perform any type of maintenance in the Production Mattermost Kubernetes Cluster which is running on AWS using the EKS.


## Setup local environment to access K8s

First if you don't have `kubectl` installed you will need to install, also if your `kubectl` is older then version 1.10 you need to update.

Also you will need the AWS Keys for the Main Mattermost AWS account. You can get one using Onelogin, please follow this [instructions](../../onelogin-aws)

### To install kubectl on MacOS

```Bash
$ brew install kubernetes-cli
```

Also you can download the AWS kubectl:

```Bash
$ curl -o kubectl https://amazon-eks.s3-us-west-2.amazonaws.com/1.10.3/2018-07-26/bin/darwin/amd64/kubectl

$ chmod +x ./kubectl
$ mkdir $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$HOME/bin:$PATH
$ echo 'export PATH=$HOME/bin:$PATH' >> ~/.bash_profile
```

To check the kubectl version:

```Bash
$ kubectl version --short --client
```

### Configure kubectl for Amazon EKS

Follow the instructions in this [page](https://docs.aws.amazon.com/eks/latest/userguide/configure-kubectl.html)

### Create a kubeconfig for Amazon EKS

Follow the instructions in this [page](https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html)

NOTE: Please talk with Carlos to get the cluster name.


### Check if you can see the pods

To check if you can see the pods in the K8s cluster, you can check doing this:

```Bash
$ kubectl get po -n community
NAME                                              READY   STATUS    RESTARTS   AGE
mattermost-community-0                            1/1     Running   0          5h
mattermost-community-1                            1/1     Running   0          23h
mattermost-community-jobserver-65985bfc47-88qq9   1/1     Running   0          5h
```



# Troubleshooting

