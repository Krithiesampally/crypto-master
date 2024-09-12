# Deploying Static Website using Load Balancer by ARM Template

## Project Overview

A new digital currency that lets people send and receive money securely and privately.

## Problem Statement

Create a cryptocurrency that provides a high potential for returns on investment, while maintaining a stable and secure platform for users to buy, sell, and trade. The cryptocurrency should be designed to attract investors and traders looking for profitable opportunities, while also ensuring the long-term sustainability and growth of the platform.
## Project Goals

- Deploy the *crypto-master* website on Azure using ARM templates.
- Set up a *Virtual Network (VNet)* with two *Subnets* and a *Network Security Group (NSG)*.
- Use a *Load Balancer* to distribute traffic between two VMs located in different availability zones.
- Host the static website on these VMs and make it accessible via the load balancer's frontend IP.

## Technologies and Azure Services Used

1. *Azure CLI*: Used to create the resource group and Virtual Network.
2. *ARM Templates*: Automated the creation of VNet, subnets, and NSG.
3. *Azure Virtual Machines (VMs)*: Hosted the Closet.AI website.
4. *Azure Load Balancer*: Distributed the traffic between two VMs to ensure high availability.
5. *Nginx*: Used as a web server on both VMs to serve the static content.
6. *Git*: Cloned the website from GitHub onto the VMs using a custom script.
7. *Custom Script Extension*: Used to automatically configure the VMs upon deployment.

## Project Steps

### 1. Website Development
- *Cryptocurrency*: A static website allowing users to kickstart there career in investing.
### 2. Deploying the Website on GitHub
- The frontend of *crypto master* was uploaded to a public GitHub repository: [crypto-master](https://github.com/Krithiesampally/crypto-master.git)

### 3. Azure Deployment Using ARM Templates
- *Resource Group*: Created using Azure CLI to hold all the resources.
- *Virtual Network (VNet)*: Set up using an ARM template, which included two subnets for distributing the VMs.
- *Network Security Group (NSG)*: Applied inbound rules to allow traffic on ports 22 (SSH) and 80 (HTTP).
  
### 4. Virtual Machines Setup
- *VM 1*: Created in Availability Zone 1 using Azure Portal. Configured with:
  - Custom Script Extension to clone the website from GitHub.
  - Networking settings to connect to the VNet and assigned Subnet.
  
  Custom Script:
  ```bash
  #!/bin/bash
  sudo apt update
  sudo apt install nginx git -y
  cd /tmp && git clone https://github.com/Krithiesampally/crypto-master.git crypto-master
  sudo rm -rf /var/www/html/index.nginx-debian.html
  sudo cp -r /tmp/crypto-master/* /var/www/html
  ```
  
  

- *VM 2*: Created in Availability Zone 3 with the same configuration as VM 1.

### 5. Load Balancer Configuration
- *Load Balancer*: Configured to distribute traffic between VM 1 and VM 2.
  - *Frontend IP Configuration*: Assigned a new frontend IP for external access.
  - *Backend Pool*: Added both VMs to the backend pool for traffic distribution.
  - *Load Balancing Rule*: Defined to balance HTTP traffic (port 80) across the VMs.
  - *Health Probe*: Set up to monitor the health of the VMs and ensure traffic is routed only to healthy VMs.

### 6. Testing and Accessing the Website
- After the load balancer deployment, the website became accessible via the frontend IP of the load balancer. Users can interact with *crypto-master* to invest in bitcoins.


## Azure Services and Tools Used

- *Azure CLI*: Resource group creation and management.
- *Azure Resource Manager (ARM) Templates*: Infrastructure-as-Code to deploy resources.
- *Virtual Network (VNet)*: Networking and subnetting.
- *Network Security Group (NSG)*: Security rules for VM access.
- *Azure Virtual Machines*: Hosting the website on multiple VMs.
- *Azure Load Balancer*: Load balancing between VMs.
- *Nginx*: Web server for hosting static content.
- *Git*: Version control and cloning the website onto VMs.
- *Custom Script Extension*: Automated configuration of VMs.

## Live Website and Resources

- *Website Link*: [Healthcare Services](https://github.com/Indhu2024/Website.git)
  
- *Screenshots*:
  *Created Resource Group Screenshot*
  - ![ResourceGroup Screenshot](ProjectScreenshots/ResourceGroupSS.png)
    
  *ResourceGroup Deployment Command Output*
  - ![RSG-Deployment-output Screenshot](ProjectScreenshots/RSG-Deployment-output.png)
 
   *Deployed VM 1 Screenshot*
  - ![VM1SS Screenshot](./ProjectScreenshots/VM1SS.png)

  *Deployed VM 2 Screenshot*
  - ![VM2SS Screenshot](./ProjectScreenshots/VM2SS.png)

  *Deployed LoadBalancer Screenshot*
  - ![LoadbalancerSS Screenshot](./ProjectScreenshots/LoadbalancerSS.png)

  *Website Home Page Screenshot*
  - ![closet.AIHomepage Screenshot](ProjectScreenshots/HomePage.png)

  *Whatsapp Integration  Page after complete Deployment*
  - ![Whatsapp ](ProjectScreenshots/Whatsapp.png)


## Conclusion

This project showcases the end-to-end process of deploying a static website using Azure's ARM templates and load balancing capabilities. By distributing traffic between two VMs in different availability zones, we ensure high availability and scalability for the *crypto-master* platform. The integration of Azure's powerful tools and services simplified the deployment and configuration process.

## Author

*Jayanthi kumari*  
*Krithi*
*Yousuf*
Deployed all group members together as part of learning Azure's cloud infrastructure.
