# Elsa-Clark-PJ-1
Project 1 

# Cloud Network  


This outlines my first project, which is a collection of Linux Scripts and Ansible Scripts from my Cyber Security Bootcamp (George Washington University). 
Many of the scripts were used to configure cloud servers with docker containers. 

The final step will show (4) servers that were running vulnerable DVWA containers along with a jump box and a server running on ELK Stack.  


# ELK STACK DEPLOYMENT 

The files in this repository were used and tested to configured a network in generating an Elk Deployment using Azure. The files can be used to recreate the entire network deployment, or only certain pieces of it, such as Filebeat.
This document contains the following details:

Network Diagram
Description of the Topology
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
Ansible Build

# Description of the Topology
JBP - (Jumpbox)
The jumpbox acts as a gateway router that is exposed to the public internet. It sits in front of all other machines that are not exposed to the internet. Directing all traffic through this one node drastically reduces the attack surface. We can implement strong access controls to this single machine, instead of on every VM.

 # LB - (Load Balancer)
The load balancer distributez traffic evenly and ensures the application will be available. It also restricts inbound access into the network. The Health Probe function detects faiure of an application on the backnd endpoint. It can also be used to for flow control to manage load or planned downtime. 

# ELK-Server (Elasticsearch, Logstash, Kibana)
ELK is the three open source projects: (Elasticsearch, Logstash, and Kibana). Elasticsearch is a search and analytics engine server allowing us to easily monitor the vulnerable Virtual Machines (VMs) for changes to the file systems of the VMs on the network and system metrics.

# Web-1 Web-2 Web-3 (Virtual Web Servers)
There are three web servers that checks for redundancy so if one is not working or goes down, there are two others availble.

# Red-Team-Avail-Set (Availability Set)
The web servers are part of an Availability Set, a fault-tolerant group of VMs. Multiple servers are often used to make the website more resilient.

# Peer to Peer Connections 
Peer-to-peer network connections (peerings) are configured between the two virtual networks. Operating as one, traffic is allowed between them. Files can be shared between the system and allows for the machines to communication with each other.

# Red-Team-Network Security Groups - ELK
Firewalls are built to protect a network. It also is used to block and allow traffic to the virtual network and between machines on the network.

# Configuration Details:  
[image](https://user-images.githubusercontent.com/71534804/115162925-4a695680-a074-11eb-9514-7ac40198d4d7.png)
 
 
 
 
 
 
# Elk Configuration
Ansible was used to configuration the ELK machine. There was no manul configuration which allowed the information to be replicated. 
The playbook install_elk.yml implements the following tasks:
Install docker
Install python3
Increase virtual memory
Download and launch a docker elk container
Enable service docker on boot 

The screenshot below shows the result of running docker ps and after successful configuring the ELK instance 
 
 <img width="1062" alt="docker ps " src="https://user-images.githubusercontent.com/71534804/115163266-36beef80-a076-11eb-9deb-b61db6175a56.png">

 
 
 
 
# Beats
The fllowing BEATS was installed on the machines:

Filebeat with playbook install_filebeat.yml
Metricbeat with playbook install_metricbeat.yml
Using Beats, we are able to collect the follwing information form each machine: 
Filebeat monitors the log files or locations that is specified ou specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.Metricbeat takes metric and statistics from your system that is collected and send them into an output that is specified the machines metrics such as CPU usage, for example usage too high.
Machines Being Monitored
This ELK server is configured to monitor the following machines:

10.0.0.6
10.0.0.7
10.0.0.8
# How to Use the Ansible Build
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

Copy the playbook "install_elk" to /etc/ansible/
Update the hosts file with IP address of each VM to run the playbook on.
Run the playbook and navigate to http://[your.Elk.VM.IP]:5601/app/kibana from your browser to check that the installation worked as expected.
 
 
