# argo-gitops-sample

## Overview
A sample GitOps project for OpenShift utilizing Standalone ArgoCD or Argo running on RHACM (Red Hat Advanced Cluster Manager).

This repo can be used in two ways.  

1. Argo running on RHACM
    1. This setup allows a single Argo instance (running on an RHACM hub) to configure multiple managed clusters
2. Argo running on a single cluster without RHACM (Standalone)
    1. This setup requires an Argo instance on every cluster


## Installation - Argo on RHACM

### Setup RHACM

```bash
# Log in to the hub cluster with cluster-admin

# cd to git source location, eg
# cd ~/git/argo-gitops-sample

# Install RHACM Operator Prerequisites
oc apply -k cluster/manifests/rhacm/base

# Install OpenShift GitOps Operator
oc apply -k cluster/manifests/argocd/base

# wait for the Operator to install

# Configure RHACM
oc apply -k cluster/manifests/rhacm/overlays/local-cluster

```

### Setup GitOps Application

```bash
oc apply -f argo-applications/local-cluster/application.yaml
```

## Installation - Standalone Argo

### Setup Argo

```bash
# Log in to the cluster with cluster-admin

# cd to git source location, eg
# cd ~/git/argo-gitops-sample

# Install OpenShift GitOps Operator
oc apply -k cluster/manifests/argocd/base

# wait for the Operator to install
```

### Setup GitOps Application

```bash
oc apply -f argo-applications/local-cluster/application.yaml
```
