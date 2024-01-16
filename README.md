# This guide will walk you through the process of setting up Wazuh, a security information and event management (SIEM) tool, on a server and its corresponding agent on a client.

## Server Setup
## Step 1: Prerequisites
Make sure you have the following prerequisites for your server:

 - Ubuntu 20.04 (or your preferred Linux distribution)
 - Internet connection
 - sudo access
## Step 2: Install Wazuh Manager
Run the following commands to install the Wazuh Manager:

- ```curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && sudo bash ./wazuh-install.sh -a```
- ```sudo apt-get update```
- ```sudo apt-get install wazuh-manager```
- Once the installation of the server is finished. It will provide a link to the dashboard and login credentials:
<br> This is the ipv4 of the wazuh server. You can find this by typing "ip a s" in the terminal. <br>
 ![](https://i.imgur.com/E6zV1Zd.png)
<br>Save these credentials somewhere secure, you will be using these to login to the dashboard. <br>
 ![](https://i.imgur.com/QNBMCNT.png)
- **NOTE:** If the service hasn't started automatically, go ahead and start it manually with the following command:
<br>```sudo systemctl start wazuh-manager```

## Step 3: 


## Step 4: Install Wazuh API and Dashboard
Run the following commands:

```sudo apt-get install wazuh-api```
```sudo apt-get install wazuh-dashboard```

Step 5: Access Wazuh Dashboard
Open a web browser and navigate to http://your-server-ip:5601 to access the Wazuh dashboard.

Client (Agent) Setup
Step 1: Prerequisites
Make sure you have the following prerequisites installed on your client:

 Same Linux distribution as the server
 Internet connection
 sudo access
Step 2: Download Wazuh Agent
Download the Wazuh agent for your architecture from the official website: Wazuh Downloads

Step 3: Install Wazuh Agent
Install the Wazuh agent using the downloaded package. Replace [wazuh-agent-package.deb] with the actual package name.

bash
Copy code
sudo dpkg -i [wazuh-agent-package.deb]
Step 4: Configure Wazuh Agent
Edit the Wazuh agent configuration file /var/ossec/etc/ossec.conf and configure the Wazuh manager IP address.

bash
Copy code
sudo nano /var/ossec/etc/ossec.conf
Step 5: Restart Wazuh Agent
Restart the Wazuh agent for changes to take effect:

bash
Copy code
sudo systemctl restart wazuh-agent
