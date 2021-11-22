# Learn Terraform - Provision an EKS Cluster
https://learn.hashicorp.com/tutorials/terraform/eks

This repo is a companion repo to the [Provision an EKS Cluster learn guide](https://learn.hashicorp.com/terraform/kubernetes/provision-eks-cluster), containing

Terraform configuration files to provision an EKS cluster on AWS.

1. vpc.tf provisions a VPC, subnets and availability zones using the AWS VPC Module. A new VPC is created for this tutorial so it doesn't impact your existing cloud environment and resources.

2. security-groups.tf provisions the security groups used by the EKS cluster.

3. eks-cluster.tf provisions all the resources (AutoScaling Groups, etc...) required to set up an EKS cluster using the AWS EKS Module.

Configure kubectl
Now that you've provisioned your EKS cluster, you need to configure kubectl.

Run the following command to retrieve the access credentials for your cluster and automatically configure kubectl.

aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)



https://registry.terraform.io/providers/hashicorp/aws/2.52.0/docs/resources/eks_cluster