# Operator Lifecycle Manager module

This is a fork of [cloud-native-toolkit/terraform-k8s-olm](https://github.com/cloud-native-toolkit/terraform-k8s-olm), published to the Terraform module registry.

Installs Operator Lifecycle Manager (OLM) into a cluster. However, if the cluster is OpenShift 4.x
and already has OLM installed then the module does not install anything. It can still be used to export
the olm namespaces for use by downstream modules.

## Supported cluster types

* ocp3
* ocp4
* kubernetes

## Example usage

```hcl-terraform
module "olm" {
  source = "Keanu73/olm/k8s"
  version = "0.1.0"

  cluster_config_file      = "~/.kube/config"
  cluster_version          = "3.11"
  cluster_type             = "ocp3"
}
```

Another example

```hcl-terraform
module "olm" {
  source = "Keanu73/olm/k8s"
  version = "0.1.0"

  cluster_config_file      = module.dev_cluster.config_file_path
  cluster_version          = module.dev_cluster.version
  cluster_type             = var.cluster_type
}
```
