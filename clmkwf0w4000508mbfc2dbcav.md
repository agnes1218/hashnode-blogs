---
title: "TerraWeek Day 6: Terraform Providers"
datePublished: Fri Sep 15 2023 17:53:49 GMT+0000 (Coordinated Universal Time)
cuid: clmkwf0w4000508mbfc2dbcav
slug: terraweek-day-6-terraform-providers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694800400096/47c0cfc4-82eb-4b97-a11e-6503f7923ebe.png
tags: devops, terraform, trainwithshubham, tws, terraweekchallenge

---

Welcome to **Day 6** of the TerraWeek challenge!

🚀 In today's tasks, we will explore **Terraform providers** and their role in interacting with different cloud platforms or infrastructure services. We will also dive into provider configuration, authentication, and hands-on practice using providers for platforms such as **AWS**, **Azure**, **Google Cloud**, or others.

## Task 1: Learn and Compare Terraform Providers

✨ **Objective**: Learn about Terraform providers and compare their features across different cloud platforms.

Terraform providers are plugins that allow Terraform to interact with various cloud providers, services, and external systems. Each provider is responsible for understanding the APIs and behaviors of a specific infrastructure platform or service. Terraform providers are essential for creating, managing, and updating resources in those platforms. Here's an overview of Terraform providers and a comparison of their features across different cloud platforms:

1. **What Are Terraform Providers?**
    
    * Terraform providers are responsible for translating your Terraform code into API calls for various infrastructure services or platforms.
        
    * Each provider is specific to a particular service, such as AWS, Azure, Google Cloud, Docker, or Kubernetes.
        
2. **Provider Configuration:**
    
    * In your Terraform configuration files (typically with a `.tf` extension), we define which provider to use and configure it.
        
    * Provider configurations include details like access credentials, regions, and other service-specific settings.
        
3. **Resource Definitions:**
    
    * Providers offer a wide range of resource types that we can manage using Terraform. Resources are infrastructure components like virtual machines, databases, or networks.
        
    * We define these resources in our Terraform configuration, specifying their attributes and relationships.
        
4. **Resource Dependencies:**
    
    * Terraform uses a dependency graph to determine the order in which resources should be created, updated, or destroyed based on their dependencies.
        
    * We express these dependencies within our configuration, allowing Terraform to orchestrate resource provisioning correctly.
        
5. **State Management:**
    
    * Terraform keeps track of the state of your infrastructure using a state file.
        
    * This state file, often stored remotely for collaboration and safety, records the current configuration and status of resources.
        
6. **Initialization and Execution:**
    
    * Run `terraform init` to initialize your working directory and download the necessary provider plugins.
        
    * Use `terraform plan` to generate an execution plan based on your configuration.
        
    * Apply changes `terraform apply` after reviewing the plan.
        

### **AWS (EC2 Instance on AWS):**

* Virtually AWS services and resources are supported.
    
* Commonly used resources include EC2 instances, S3 buckets, RDS instances, VPCs, security groups, and IAM roles.
    
* In-depth support for IAM policies and roles.
    

### **AWS Example (EC2 Instance on AWS):**

```yaml
hclCopy code# Configure the AWS provider
provider "aws" {
  region = "us-east-1"
}

# Create an EC2 instance
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"  # Amazon Linux 2
  instance_type = "t2.micro"
  tags = {
    Name = "MyInstance"
  }
}

# Output the public IP address of the EC2 instance
output "public_ip" {
  value = aws_instance.example.public_ip
}
```

In this AWS example, we configure the AWS provider, create an EC2 instance, and output its public IP address.

### **Azure Example (Virtual Machine on Azure):**

```yaml
hclCopy code# Configure the Azure provider
provider "azurerm" {
  features {}
}

# Create an Azure virtual machine
resource "azurerm_virtual_machine" "example" {
  name                  = "myVM"
  location              = "East US"
  resource_group_name   = "myResourceGroup"
  network_interface_ids = [azurerm_network_interface.example.id]

  vm_size              = "Standard_DS2_v2"
  delete_os_disk_on_termination = true

  storage_os_disk {
    name              = "myOsDisk"
    caching           = "ReadWrite"
    create_option     = "FromImage"
    managed_disk_type = "Premium_LRS"
  }

  storage_image_reference {
    publisher = "Canonical"
    offer     = "UbuntuServer"
    sku       = "18.04-LTS"
    version   = "latest"
  }

  os_profile {
    computer_name  = "hostname"
    admin_username = "adminuser"
    admin_password = "Password1234!"
  }
}
```

In this Azure example, we configure the AzureRM provider, create a virtual machine, and define its properties.

### **Google Cloud Example (Compute Engine on GCP):**

```yaml
hclCopy code# Configure the Google Cloud provider
provider "google" {
  credentials = file("path/to/your/credentials.json")
  project     = "your-project-id"
  region      = "us-central1"
}

# Create a Google Compute Engine instance
resource "google_compute_instance" "example" {
  name         = "my-instance"
  machine_type = "n1-standard-1"
  zone         = "us-central1-a"

  boot_disk {
    initialize_params {
      image = "debian-cloud/debian-9"
    }
  }

  network_interface {
    network = "default"
  }
}
```

<table><tbody><tr><td colspan="1" rowspan="1"><p><strong>Terraform Provider</strong></p></td><td colspan="1" rowspan="1"><p><strong>Features</strong></p></td><td colspan="1" rowspan="1"><p><strong>Supported Resources</strong></p></td></tr><tr><td colspan="1" rowspan="1"><p>Terraform AWS Provider</p></td><td colspan="1" rowspan="1"><p>Supports a wide range of AWS resources, including EC2 instances, S3 buckets, RDS databases, and more.</p></td><td colspan="1" rowspan="1"><p>Supports over 200 AWS resources.</p></td></tr><tr><td colspan="1" rowspan="1"><p>Terraform Azure Provider</p></td><td colspan="1" rowspan="1"><p>Supports a wide range of Azure resources, including virtual machines, storage accounts, SQL databases, and more.</p></td><td colspan="1" rowspan="1"><p>Supports over 150 Azure resources.</p></td></tr><tr><td colspan="1" rowspan="1"><p>Terraform GCP Provider</p></td><td colspan="1" rowspan="1"><p>Supports a wide range of GCP resources, including compute engine instances, cloud storage buckets, cloud SQL databases, and more.</p></td><td colspan="1" rowspan="1"><p>Supports over 100 GCP resources.</p></td></tr><tr><td colspan="1" rowspan="1"><p>Terraform Kubernetes Provider</p></td><td colspan="1" rowspan="1"><p>Supports the creation and management of Kubernetes clusters and resources.</p></td><td colspan="1" rowspan="1"><p>Supports the creation and management of Kubernetes clusters, nodes, pods, and more</p></td></tr></tbody></table>

1. **Authentication:** Distinct authentication procedures are needed for every supplier. Here are a few typical methods of authentication for well-known Terraform providers:
    

* **Access keys, or API keys,** are used for authentication by several services, including AWS and Azure. Normally, you provide these keys in the provider block as configuration settings. Make sure you handle and safeguard these keys securely.
    
* **Service account credentials** are frequently used by providers like GCP. As a configuration option in the provider block, you can indicate the location of the service account key file.
    
* **Authentication Tokens**: Certain providers, like GitHub or GitLab, may require authentication tokens. These tokens are usually obtained from the provider's web interface, and you can provide them as configuration settings in the provider block.
    
* **Configuration Files**: Providers like Kubernetes or Docker may rely on configuration files, such as the kubeconfig file for Kubernetes or the Docker configuration file. Specify the path to these configuration files as configuration settings in the provider block.
    
    **AWS Provider Configuration:**
    

```yaml
provider "aws" {
  region     = "us-west-2"
  access_key = "YOUR_ACCESS_KEY"
  secret_key = "YOUR_SECRET_KEY"
}
```

**Azure Provider Configuration:**

```yaml
provider "azurerm" {
  features {}
  subscription_id = "YOUR_SUBSCRIPTION_ID"
  client_id       = "YOUR_CLIENT_ID"
  client_secret   = "YOUR_CLIENT_SECRET"
  tenant_id       = "YOUR_TENANT_ID"
}
```

## Task 2: Provider Configuration and Authentication

In Terraform, provider configuration is an essential aspect of defining how to interact with various cloud providers or services.

**Provider Block**: You typically start by defining a provider block for the desired cloud provider in your Terraform configuration. This block specifies the provider's name and version, and it may include other provider-specific settings.

```yaml
 provider "aws" {
   region     = "us-east-1"
 }
```

1. In this example, the provider block configures Terraform to interact with AWS services in the `us-east-1` region.
    
2. **Authentication**: Providers often require authentication credentials to access resources. Authentication mechanisms vary depending on the provider. Some common authentication methods include:
    
3. **Access Keys**: For AWS, you can provide access and secret keys as environment variables, in configuration files, or use IAM roles.
    
    * **Service Account Keys**: Google Cloud uses service account JSON key files.
        
    * **Client IDs and Secrets**: For OAuth2-based authentication with providers like Azure or Google Cloud.
        
    * **SSH Key Pairs**: For providers that require SSH authentication.
        
    
    It's essential to secure these credentials properly, often by using environment variables, credential files, or external vaults.
    
    1. **Environment Variables**: You can set authentication credentials using environment variables. Terraform supports specific environment variable names recognized by each provider. For example, AWS credentials can be set using `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`.
        
    2. **Credential Files**: For providers that use credential files, you can specify the file's path directly in the provider block. Ensure that these files are kept secure.
        

```yaml
provider "example" {
  endpoint    = "https://api.example.com"
  access_key  = "YOUR_ACCESS_KEY"
  secret_key  = "YOUR_SECRET_KEY"
  region      = "us-east-1"
}
```

* **Authentication Tokens**: Certain providers, like GitHub or GitLab, may require authentication tokens. These tokens are usually obtained from the provider's web interface, and you can provide them as configuration settings in the provider block.
    
* **Configuration Files**: Providers like Kubernetes or Docker may rely on configuration files, such as the kubeconfig file for Kubernetes or the Docker configuration file. Specify the path to these configuration files as configuration  
    
* **AWS Provider Configuration:**
    

```yaml
provider "aws" {
  region     = "us-west-2"
  access_key = "YOUR_ACCESS_KEY"
  secret_key = "YOUR_SECRET_KEY"
}
```

**Azure Provider Configuration:**

```yaml
provider "azurerm" {
  features {}
  subscription_id = "YOUR_SUBSCRIPTION_ID"
  client_id       = "YOUR_CLIENT_ID"
  client_secret   = "YOUR_CLIENT_SECRET"
  tenant_id       = "YOUR_TENANT_ID"
}
```

**Setting up authentication for each Terraform provider on your local machine involves configuring the necessary credentials to interact with specific cloud platforms. Here's a general guide on how to set up authentication for some popular cloud providers:**

**Amazon Web Services (AWS)**:

* **Access and Secret Keys**: You can configure AWS access and secret keys to authenticate with AWS services. These keys can be obtained from the AWS IAM (Identity and Access Management) console.
    
    ```yaml
      export AWS_ACCESS_KEY_ID=your-access-key-id
      export AWS_SECRET_ACCESS_KEY=your-secret-access-key
    ```
    
    * **Named Profiles**: AWS also supports named profiles that you can configure in the `~/.aws/credentials` file. For example, you can create a profile named `myprofile`:
        
        ```yaml
          [myprofile]
          aws_access_key_id = your-access-key-id
          aws_secret_access_key = your-secret-access-key
        ```
        
        **Google Cloud Platform (GCP)**:
        
    * **Service Account JSON Key**: To authenticate with GCP, you'll need a service account JSON key. Create a service account in the GCP Console and download the JSON key file.
        
        1. * ```yaml
                  export GOOGLE_APPLICATION_CREDENTIALS=/path/to/your/key.json
                ```
                

**Microsoft Azure**

* **Service Principal**: To authenticate with Azure, you can create a service principal and use its credentials. Use the Azure CLI to create a service principal:
    
    ```yaml
      az ad sp create-for-rbac --name ServicePrincipalName
    ```
    
    This command will output a JSON object with the required credentials. Store them securely.
    
    ```yaml
      export ARM_CLIENT_ID=your-client-id
      export ARM_CLIENT_SECRET=your-client-secret
      export ARM_SUBSCRIPTION_ID=your-subscription-id
      export ARM_TENANT_ID=your-tenant-id
    ```
    

## Task 3: Practice Using Providers

1. **Create a Terraform configuration file named** [**main.tf**](http://main.tf) **and configure the chosen provider within it.**
    
    ```yaml
    # Configure the AWS provider
    provider "aws" {
      region     = "us-east-1"
      access_key = "YOUR_ACCESS_KEY"
      secret_key = "YOUR_SECRET_KEY"
    }
    
    # Create an EC2 instance
    resource "aws_instance" "example" {
      ami           = "ami-0c55b159cbfafe1f0"  # Amazon Linux 2
      instance_type = "t2.micro"
      tags = {
        Name = "MyInstance"
      }
    }
    
    # Output the public IP address of the EC2 instance
    output "public_ip" {
      value = aws_instance.example.public_ip
    }
    ```
    

1. **Authenticate with the chosen cloud platform**
    

To authenticate AWS we use the AWS Configure command we need to add an access key and secret key.

Then we need to run the terraform commands

**Terraform init** -Initialize the Terraform working directory. This command downloads the necessary provider plugins and sets up the backend for storing the Terraform state.

**Terraform plan** - The "terraform plan" command is used in Terraform to create an execution plan

**Terraform apply** - The "terraform apply" command is used in Terraform to apply the changes defined in your Terraform configuration files to your infrastructure.

***Happy Learning!***