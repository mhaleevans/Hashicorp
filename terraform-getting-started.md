# Getting Started with Terraform

Terraform is the most popular language for defining and provisioning infrastructure as code (IaC).

<!-- I would question making this kind of unsupported statement. -->

In this guide, you will
- Install Terraform.
- Create a configuration code file.
- Initialize Terraform and provision the resource.
- Destroy the infrastructure.


## Prerequisites

- Internet access
- Command-line interface for your machine

## Install and configure Terraform

To install Terraform, visit [Terraform.io](https://www.terraform.io/downloads.html) and download the compressed binary application executable file deliverable for your preferred platform, machine, or environment.

With Terraform installed, you're ready to create some infrastructure.

<!-- I'm not sure the above is necessary, but it's still a good transition. -->

We recommend that you create a new directory on your local machine and then create Terraform configuration code inside it.

```shell
$ mkdir terraform-demo
$ cd terraform-demo
```

Next, create a file for your Terraform configuration code.

```shell
$ touch main.tf
```

Copy and paste the following lines into the file.

```hcl
provider "docker" {
    host = "unix:///var/run/docker.sock"
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.latest
  name  = "training"
  ports {
    internal = 80
    external = 80
  }
}

resource "docker_image" "nginx" {
  name = "nginx:latest"
}
```

## Initialize Terraform, provision the resource, and destroy the infrastructure

Initialize Terraform with the `init` command. Terraform will install the AWS provider. 

<!-- Would it be necessary to call out the AWS acronym? -->

```shell
$ terraform init
```

Check for errors. If you don't find any errors, provision the resource with the `apply` command.

```shell
$ terraform apply
```

The command will take up to a few minutes to run. After finishing, it will display a message indicating that it has created the resource.

Finally, destroy the infrastructure.

```shell
$ terraform destroy
```

When you see a message at the bottom of the output asking for confirmation, type `yes` and then ENTER. Terraform will destroy the resources it created earlier.

## Next steps

In this guide, you installed and configured Terraform, and then you initialized Terraform, provisioned the resource, and destroyed infrastructure. Now you are ready to learn about Terraform's core features, the [Terraform CLI](https://www.terraform.io/docs/cli-index.html).

For basic information about Terraform, see [Introduction to Terraform](https://www.terraform.io/intro/index.html).

For further in-depth information and ideas, see [Terraform Documentation](https://www.terraform.io/docs/index.html).

