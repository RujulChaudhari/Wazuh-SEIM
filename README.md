# This guide will walk you through the process of setting up Wazuh, a security information and event management (SIEM) tool, on a server and its corresponding agent on a client.

# <ins> Server Setup
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
- **NOTE:** If the service hasn't started automatically, go ahead and start it manually with the following command: <br>
<br>```sudo systemctl start wazuh-manager```

## Step 3: Checking all services
- Once you've installed the wazuh server. Double check that all service are running with the following command.
```sudo systemctl list-units | grep wazuh```
- You should see the wazuh-dashboard, wazuh-indexer, and wazuh-manager services running. These are the 3 main services that need to be installed and running.<br>
![](https://i.imgur.com/qjNUbxK.png)

## Step 4: Access Wazuh Dashboard
Open a web browser and navigate to http://your-server-ip:443 to access the Wazuh dashboard. This will be where you will be able to view all the logs and security events.

# <ins> Client (Agent) Setup
## Step 1: Prerequisites
- sudo access

## Step 2: Download Wazuh Agent
- On your dashboard you will see this message:
![](https://i.imgur.com/yY8dmvA.png)
- You want to go ahead and click "Add Agent". This will direct you to another page where it will give you steps on adding the actual agent.
- Here you want to select the OS.
- For simplicity sake I'll be using a ubuntu OS to setup the agent on. You can use whichever OS you prefer, the process is more or less the same.
- For the Server adress, you will be entering the ipv4 of the actual linux server.
![](https://i.imgur.com/5gVqT3X.png)
- At the bottom you will see a long command, this will be what you will run on you client machine in order to install the agent.
![](https://i.imgur.com/Sl2v82G.png)
- Once you've installed the agent on ur machine, go ahead and run the command under that in order to start the services.
![](https://i.imgur.com/l9smhc7.png)

## Step 3: Dashboard
- Now if you go back to your wazuh dashboard, you will see our agent is showing up under the agent list.
![](https://i.imgur.com/OvibfOv.png)
- You have now successfully setup both the wazuh server and agent. As long as both are up and running you will be able to veiw all the logs and security events on the dashboard. Feel free to mess around in there. Enjoy! 
