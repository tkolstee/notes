
```toc
```

## Installing
Install from [Terraform](https://developer.hashicorp.com/terraform/downloads) or use Homebrew for OSX.

## Creating a Basic Terraform Template
Create a file with `.tf` extension

### Define a Provider
```JSON
provider "aws" {
	region = "us-east-1"
	access_key = "my_access_key"
	secret_key = "my_secret_key"
}
```

### Define a Resource
```JSON
/**
resource "<provider>_<resource_type>" "name" {
	key = "value"
	key2 = "value2"
}
*/

resource "aws_instance" "testserver" {
  ami           = "ami-08c40ec9ead489470" # Ubuntu Server 22.04 LTS
  instance_type = "t2.micro"
  user_data = <<-EOF
     sudo apt update && apt -y install apache2
     sudo systemctl enable apache2
     sudo systemctl start apache2
     sudo bash -c 'echo "Hello, world!" > /var/www/html/index.html'
     EOF  
}
```

### Referencing Other Resources
```JSON
resource "aws_vpc" "first-vpc" {
    cidr_block = "10.0.0.0/16"
    tags = {
        "Name" = "production"
    }
}

resource "aws_subnet" "subnet-1" {
	// plugin_type.resource_name.attribute
    vpc_id = aws_vpc.first-vpc.id
    cidr_block = "10.0.1.0/24"
    tags = {
        Name = "prod-subnet"
    }
}
```

#### Resource Blocks

_Resources_ are the most important element in the Terraform language. Each resource block describes one or more infrastructure objects, such as virtual networks, compute instances, or higher-level components such as DNS records.

-    documents the syntax for declaring resources.
    
-   [Resource Behavior](https://www.terraform.io/language/resources/behavior) explains in more detail how Terraform handles resource declarations when applying a configuration.
    
-   The Meta-Arguments section documents special arguments that can be used with every resource type, including [`depends_on`](https://www.terraform.io/language/meta-arguments/depends_on), [`count`](https://www.terraform.io/language/meta-arguments/count), [`for_each`](https://www.terraform.io/language/meta-arguments/for_each), [`provider`](https://www.terraform.io/language/meta-arguments/resource-provider), and [`lifecycle`](https://www.terraform.io/language/meta-arguments/lifecycle).
    
-   [Provisioners](https://www.terraform.io/language/resources/provisioners/syntax) documents configuring post-creation actions for a resource using the `provisioner` and `connection` blocks. Since provisioners are non-declarative and potentially unpredictable, we strongly recommend that you treat them as a last resort.


`````ad-example
title: Basic Config - Azure RG, Network, Server
collapse: true
terraform.tfvars
```
resource_group_name = "bookRg"
application_name = "book"
```

variables.tf
```
variable "resource_group_name" {
  description = "Name of the resource group"
}
variable "location" {
  description = "Location of the resource"
  default     = "East US"
}
variable "application_name" {
  description = "Name of the application"
}
```

Provider.tf
```
provider "azurerm" {
  features {
  }
}
```

Rg.tf
```
resource "azurerm_resource_group" "rg" {
  name     = var.resource_group_name
  location = var.location
 tags = {
    environment = "Terraform Azure"
  }
}
```

Network.tf
```
resource "azurerm_virtual_network" "vnet" {
  name                = "book-vnet"
  location            = var.location
  address_space       = ["10.0.0.0/16"]
  resource_group_name = azurerm_resource_group.rg.name
}
resource "azurerm_subnet" "subnet" {
  name                 = "book-subnet"
  virtual_network_name = azurerm_virtual_network.vnet.name
  resource_group_name  = azurerm_resource_group.rg.name
  address_prefixes     = ["10.0.10.0/24"]
}
```

Compute.tf
```
resource "azurerm_network_interface" "nic" {
  name                = "book-nic"
  location            = var.location
  resource_group_name = azurerm_resource_group.rg.name
  ip_configuration {
    name                          = "bookipconfig"
    subnet_id                     = azurerm_subnet.subnet.id
    private_ip_address_allocation = "Dynamic"
    public_ip_address_id          = azurerm_public_ip.pip.id
  }
}
resource "azurerm_public_ip" "pip" {
  name                = "book-ip"
  location            = var.location
  resource_group_name = azurerm_resource_group.rg.name
  allocation_method   = "Dynamic"
  domain_name_label   = "bookdevops"
}
resource "azurerm_storage_account" "stor" {
  name                     = "tkolsteebookstor"
  location                 = var.location
  resource_group_name      = azurerm_resource_group.rg.name
  account_tier             = "Standard"
  account_replication_type = "LRS"
}
resource "azurerm_virtual_machine" "vm" {
  name                  = "bookvm"
  location              = var.location
  resource_group_name   = azurerm_resource_group.rg.name
  vm_size               = "Standard_DS1_v2"
  network_interface_ids = ["${azurerm_network_interface.nic.id}"]
  storage_image_reference {
    publisher = "Canonical"
    offer     = "UbuntuServer"
    sku       = "16.04-LTS"
    version   = "latest"
  }
  storage_os_disk {
    name              = "book-osdisk"
    managed_disk_type = "Standard_LRS"
    caching           = "ReadWrite"
    create_option     = "FromImage"
  }
  os_profile {
    computer_name  = "VMBOOK"
    admin_username = "tony"
    admin_password = "book123*"
  }
  os_profile_linux_config {
    disable_password_authentication = false
  }
  boot_diagnostics {
    enabled     = true
    storage_uri = azurerm_storage_account.stor.primary_blob_endpoint
  }
}

```

`````

## Command Line
| Command                  | Description                                            |
| ------------------------ | ------------------------------------------------------ |
| `terraform fmt filename` | Reformat file in place for style guidelines            |
| `terraform init`         | Download and install providers and other plugins       |
| `terraform plan`         | Show what actions would be performed with `apply`      |
| `terraform apply`        | Converge existing state with desired state in template |
| `terraform destroy`      | Destroy all resources                                  |

| Switch           | Description                             |
| ---------------- | --------------------------------------- |
| `--auto-approve` | Skip "yes" prompt before making changes |

## State
`terraform.tfstate` holds state data in JSON 


----
# Sources
[Terraform Course - Automate your AWS cloud infrastructure - YouTube](https://www.youtube.com/watch?v=SLB_c_ayRMo&t=125s)
