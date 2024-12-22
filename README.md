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
* **Resource Group:** Created using Azure CLI to hold all the resources.
* **Virtual Network (VNet):** Set up using an ARM template, which included two subnets for distributing the VMs.
* **Network Security Group (NSG):** Applied inbound rules to allow traffic on ports 22 (SSH) and 80 (HTTP).

### **4. Azure Deployment Using CLI**
* **Virtual Machines:** Created using Azure CLI by adding custom Script Extension to clone the website from GitHub and Networking settings to connect to the VNet and assigned Subnet.

Custom Script:
```
#!/bin/bash
sudo apt update
sudo apt install nginx git -y
cd /tmp && git clone https://github.com/taruni1503/Restaurant_project.git mysitee
sudo rm -rf /var/www/html/index.nginx-debian.html
sudo cp -r /tmp/mysitee/* /var/www/html/
```
* **Load Balancer:** Created using Azure CLI to distributed the traffic between two VMs to ensure high availability.

### **5. Load Balancer Configuration**
* **Load Balancer:** Configured to distribute traffic between VM 1 and VM 2.
* **Frontend IP Configuration:** Assigned a new frontend IP for external access.
* **Backend Pool:** Added both VMs to the backend pool for traffic distribution.
* **Load Balancing Rule:** Defined to balance HTTP traffic (port 80) across the VMs.
* **Health Probe:** Set up to monitor the health of the VMs and ensure traffic is routed only to healthy VMs.

### **6. Testing and Accessing the Website**
After the load balancer deployment, the website became accessible via the frontend IP of the load balancer. Users can interact with Restaurant Services.

## **Screenshots:**

* ### **Resource Group Creation**
  ![rg Screenshot](https://github.com/user-attachments/assets/c1d33421-7017-41ad-b481-1a033a06cff5)

* ### **Vnet and NSG Deployment Result**
  ![vnet and nsg deployment result screenshot](https://github.com/user-attachments/assets/21ed9cf7-e513-4637-aeb8-0987af7c00a8)

* ### **Vnet Creation**
![vnet creation screenshot](https://github.com/user-attachments/assets/e784ea8e-e028-45ec-8197-bf2946412302)

* ### **NSG Creation**
![nsg creation](https://github.com/user-attachments/assets/a4284dac-2021-4d74-99d1-c9e100a724f7)

* ### **VM1 and VM2 Deployment**
![vm1 vm2 deployment](https://github.com/user-attachments/assets/3f452d08-b1cb-466b-993f-e24b2c958afa)

* ### **VM1 Creation**
![vm1 creation](https://github.com/user-attachments/assets/c233bded-930b-4070-bb65-03ea759e5f89)

* ### **VM2 Creation**
![vm2 creation](https://github.com/user-attachments/assets/195c871b-b4b6-4371-8ee4-6f58791aaed5)

* ### **Load Balancer Creation**
![load balancer](https://github.com/user-attachments/assets/908aa7f6-2dd2-453d-a012-ebf92c7aea1d)
![loadb](https://github.com/user-attachments/assets/05dafe55-7dcf-4ab4-9094-d36165472326)

* ### **Home Page**
![home](https://github.com/user-attachments/assets/a4c24f43-7237-4ace-a572-665457d92b83)

* ### **About Us**
![about](https://github.com/user-attachments/assets/681952c0-1fdb-4808-a262-d930c07aa2c7)

* ### **Category**
![category](https://github.com/user-attachments/assets/84e707fa-676f-4ad1-9ab3-7fff3bb39a32)

* ### **Menu**
![menu](https://github.com/user-attachments/assets/649d8923-7eb5-4861-a1a0-0c90f680d7e0)

* ### **Testimonals**
![testimonals](https://github.com/user-attachments/assets/064450bb-dadf-4a90-9ef4-866547d2de61)

* ### **Contact Us**
![contact](https://github.com/user-attachments/assets/e881e804-f971-4d14-a8a7-927cc07d2c77)

* ## **Website Link**: https://jazzy-treacle-43dd86.netlify.app/
* ## **Video Link**: <!--[Watch Video]-->https://drive.google.com/file/d/1Jn4seyJa953l_8mFIwvRXQvdveavM9id/view?usp=sharing


## **Conclusion**
The Green Fork restaurant website successfully bridges the gap between affordability, quality, and healthy dining. By emphasizing wholesome meals without sacrificing taste, quantity, or cost, the platform caters to health-conscious individuals who value both nutrition and budget-friendly options. With user-friendly features such as online ordering, menu transparency, and sustainability highlights, the website enhances customer engagement and satisfaction.  

This project demonstrates a commitment to delivering value to customers while aligning with modern dining trends, ensuring that eating healthy is both accessible and enjoyable for all.














