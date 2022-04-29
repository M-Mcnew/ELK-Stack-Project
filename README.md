# ELK-Stack-Project

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[Azure_Diagram](https://github.com/M-Mcnew/ELK-Stack-Project/blob/3fe9a1a3f7baadf668d547ecc67296c11f870816/Images/Azure%20network%20diagram.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Roles file may be used to install only certain pieces of it, such as Filebeat.

  [ELK Deployment](Images/elk_deployment.png)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.
The main advantage of a jumpbox is that it limits access points to the public

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logfiles and system metrics.
Filebeat watches for changes in the logfiles 
Metricbeat collect metric data from the OS as well as services running on the server

The configuration details of each machine may be found below.
### Access Policies
| Name     | Function   | IP Address    | Operating System    |   |
|----------|------------|---------------|---------------------|---|
| Jump box | Gateway    | 52.229.56.177 | Linux(ubuntu 18.04) |   |
| Web-1    | Terminal   | 10.0.0.7      | Linux(ubuntu 18.04) |   |
| Web-2    | Terminal   | 10.0.0.6      | Linux(ubuntu 18.04) |   |
| ElkNet   | ELK server | 10.2.0.6      | Linux(ubuntu 18.04) |   |

The machines on the internal network are not exposed to the public Internet. 

Only the Gateway machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
98.201.122.179

Machines within the network can only be accessed by ssh.
The Jumpbox is the only machine that can access my Elk Vm. from the IP address: 10.0.0.8

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses         |
|----------|---------------------|------------------------------|
| Jump box | Yes                 | 98.201.122.179               |
| Web-1    | No                  | 10.0.0.8, 10.2.0.6, 10.0.0.6 |
| Web-2    | No                  | 10.0.0.8, 10.2.0.6, 10.0.0.7 |
| ElkNet   | Yes                 | 10.0.0.8, 98.201.122.179     |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it removes the chance for human error

The playbook implements the following tasks:
- Install docker
- Install python3
- Increase system memory
- Download image and launch ELK

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/ELK Deployment.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.6, 10.0.0.7

We have installed the following Beats on these machines:
Filebeat

These Beats allow us to collect the following information from each machine:
Filebeat is watching syslog events. This is to watch all sudo commands, ssh logins, and the creation of new users and groups

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the .yml file to /etc/ansible.
- Update the .cfg file to include the host IP
- Run the playbook, and navigate to http://52.254.0.54:5601/app/kibana to check that the installation worked as expected.

