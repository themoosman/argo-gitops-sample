# argo-gitops-sample

## Overview
A sample GitOps project for OpenShift utilizing ArgoCD and RHACM.

This report will use ArgoCD running on the RHACM hub cluster.  The Argo instance will have a single application for each managed cluster (e.g., DC1 / DC2) to control configuration.


## Installation

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


## Removal