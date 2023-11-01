# Free Kubernetes cluster on Oracle Cloud with Terraform - Eficode modifications

This repository serves as a working improvement over the original great work done by Arnold as described below. While the original repository was supporting a short series of blog post, the ambition is now to take it a bit further and improve it with automation and adding monitoring and applications to the cluster.

The purpose is also to have a cheap, or even free, playground  for both Kubernetes and Terraform by exploring and exploiting the Oracle Cloud Free Tier.

Since the repository has been restructured by at least splitting Terraform into smaller modules, the aim is not necessarily to deliver changes back to the originial.

You are welcome to contribute by creating issues and/or Pull Requests.

# Free Kubernetes cluster on Oracle Cloud with Terraform

The repository contains a Terraform script for creating a fully functioning
Kubernetes cluster on Oracle Cloud.

The repo was created for this article: [Free Oracle Cloud Kubernetes cluster with Terraform](https://arnoldgalovics.com/oracle-cloud-kubernetes-terraform/)

## Setup in a nutshell
1. Get the following data from your Oracle Cloud account
    * User OCID
    * Tenancy OCID
    * Compartment OCID
1. Open a terminal within the `oci-infra` folder
1. Execute a `terraform init`
1. Execute a `terraform apply`
1. Create your Kubernetes configuration file using 
    ```bash
    $ oci ce cluster create-kubeconfig --cluster-id <cluster OCID> --file ~/.kube/free-k8s-config --region <region> --token-version 2.0.0 --kube-endpoint PUBLIC_ENDPOINT
    ```
1. Apply your K8S config for kubectl
    ```bash
    $ export KUBECONFIG=~/.kube/free-k8s-config
    ```
1. To verify cluster access, do a `kubectl get nodes`
1. Enjoy
