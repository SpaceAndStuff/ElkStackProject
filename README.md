## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![alt text](Images/Elk_diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  (Ansible/filebeat-playbook.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessible, in addition to restricting traffic to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box? Load balancers protect the server from being overloaded by shifting some traffic away to other servers and can help defend against DDOS attacks. Jump box provides an extra layer of security by being the only Virtual machine that can access the inner network of the server.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- What does Filebeat watch for? Filebeat monitors and collects logs and locations the user specifies
- What does Metricbeat record? it records metrics from the system and services such as MySQL

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.
| Name     | Function | IP Address             | OS           |
|----------|----------|------------------------|--------------|
| Jumpbox  | Gateway  | 10.0.0.4/ 20.25.46.118 | Ubuntu 18.04 |
| Web-1    | VM       | 10.0.0.9               | Ubuntu 18.04 |
| Web-2    | VM       | 10.0.0.10              | Ubuntu 18.04 |
| ElkStack | VM       | 10.1.0.4               | Ubuntu 18.04 |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 192.168.54.2
Machines within the network can only be accessed by jumpbox provisioner.
- jumpbox provisioner 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name     | publicly accessible | Allowed I.P addresses |
|----------|---------------------|-----------------------|
| Jumpbox  | YES                 | 192.168.54.2          |
| Web-1    | NO                  | 10.0.0.4/10.1.0.4     |
| Web-2    | NO                  | 10.0.0.4/10.1.0.4     |
| ElkStack | YES                 | 10.0.0.4/192.168.54.2 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? multiple machines can be updated simultaneously and quickly.

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- create an Elk stack VM with a minimum of 4gb of ram
- edit the Hosts file in the ansible node to specify which server the playbook will make changes to 
-create a playbook to install docker and the Elk stack container to and run it
-Make a new rule in the Network security group to deny access to outside computers to the VM

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/sebp.JPG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
 10.0.0.9/10.0.0.10
We have installed the following Beats on these machines:
- packetbeat & metricbeat

These Beats allow us to collect the following information from each machine:
 collects Windows logs, which we use to track user logon events, etc. Metricbeat can also be used to track CPU and memory usage of a system.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_ Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? the file is filebeat-playbook.yml and you copy it to /etc/ansible 
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? you have to make changes to the host file in the /etc/ansible directory, you create a group in that file and add the local I.P of the computers you want in that group. In the Playbook file you specify the group you intend to target.
- _Which URL do you navigate to in order to check that the ELK server is running? you type in https://the I.P of the Elk server and follow that with a :5601
