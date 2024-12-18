# **Deploying Static Website using Load Balancer by ARM Template**
## **Project Overview**
The **Green Fork restaurant** aims to provide an engaging, user-friendly platform that reflects the restaurant’s dedication to health, flavor, and quality. It serves as a digital representation of Green Fork’s values, emphasizing sustainability, nutrition, and culinary excellence while facilitating a seamless customer experience.The  website is designed to reflect the restaurant's mission of providing nutritious, high-quality meals without compromising on quantity or affordability. It serves as a digital platform to attract health-conscious customers who value wholesome dining options at reasonable prices, emphasizing transparency, quality, and customer satisfaction.

This project demonstrates the deployment of Green Fork restaurant website using Azure's ARM templates and load balancing across two Virtual Machines (VMs). 

## **Problem Statement**
In today's fast-paced world, many individuals struggle to find meals that are both healthy and affordable, while also meeting their expectations of quality and quantity. Existing dining options often compromise on one or more of these aspects, leaving customers dissatisfied.

## **Project Goals**
* Deploy the **Green Fork Restaurant** website on Azure using ARM templates.
* Set up a **Virtual Network (VNet)** with two **Subnets** and a **Network Security Group (NSG)**.
* Use a **Load Balancer** to distribute traffic between two VMs.
* Host the static website on these VMs and make it accessible via the load balancer's frontend IP.

## **Technologies and Azure Services Used**
* **Azure CLI:** Used to create the resource group, Virtual Network and Load Balancer.
* **ARM Templates:** Automated the creation of VNet, subnets, and NSG.
* **Azure Virtual Machines (VMs):** Hosted the Restaurant website.
* **Azure Load Balancer:** Distributed the traffic between two VMs to ensure high availability.
* **Nginx:** Used as a web server on both VMs to serve the static content.
* **Git:** Cloned the website from GitHub onto the VMs using a custom script.
* **Custom Script Extension:** Used to automatically configure the VMs upon deployment.

## **Project Steps**

### **1. Website Development**
Restaurant: A website dedicated to serving healthy, high-quality, and affordable meals without compromising on taste or quantity. 

### **2. Deploying the Website on GitHub**
The frontend of Restaurant was uploaded to a public GitHub repository.

### **3. Azure Deployment Using ARM Templates**
**Resource Group:** Created using Azure CLI to hold all the resources.
**Virtual Network (VNet):** Set up using an ARM template, which included two subnets for distributing the VMs.
**Network Security Group (NSG):** Applied inbound rules to allow traffic on ports 22 (SSH) and 80 (HTTP).

### **4. Azure Deployment Using CLI**
**Virtual Machines:** Created using Azure CLI by adding custom Script Extension to clone the website from GitHub and Networking settings to connect to the VNet and assigned Subnet.

Custom Script:
```
#!/bin/bash
sudo apt update
sudo apt install nginx git -y
cd /tmp && git clone https://github.com/taruni1503/Restaurant_project.git mysitee
sudo rm -rf /var/www/html/index.nginx-debian.html
sudo cp -r /tmp/mysitee/* /var/www/html/
```
**Load Balancer:** Created using Azure CLI to distributed the traffic between two VMs to ensure high availability.

### **5. Load Balancer Configuration**
* **Load Balancer:** Configured to distribute traffic between VM 1 and VM 2.
* **Frontend IP Configuration:** Assigned a new frontend IP for external access.
* **Backend Pool:** Added both VMs to the backend pool for traffic distribution.
* **Load Balancing Rule:** Defined to balance HTTP traffic (port 80) across the VMs.
* **Health Probe:** Set up to monitor the health of the VMs and ensure traffic is routed only to healthy VMs.

### **6. Testing and Accessing the Website**
After the load balancer deployment, the website became accessible via the frontend IP of the load balancer. Users can interact with Restaurant Services.

## **Conclusion**
The Green Fork restaurant website successfully bridges the gap between affordability, quality, and healthy dining. By emphasizing wholesome meals without sacrificing taste, quantity, or cost, the platform caters to health-conscious individuals who value both nutrition and budget-friendly options. With user-friendly features such as online ordering, menu transparency, and sustainability highlights, the website enhances customer engagement and satisfaction.  

This project demonstrates a commitment to delivering value to customers while aligning with modern dining trends, ensuring that eating healthy is both accessible and enjoyable for all.














