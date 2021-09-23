 Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO:Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible file may be used to install only certain pieces of it, such as Filebeat.

  -ELK-Stack-Project/Ansible

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


 Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available for the customers, in addition to restricting attacks to the network.
It protects the system from DDos attacks by shifting attack traffic. A jump box gives access to the user from a single node that can be secured and monitored

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
> Filebeat monitors the log files or locations specified, collects log events and forwards them either to Elasticsearch or Logstash for indexing.
> Metricbeat helps in monitoring the servers by collecting metrics from the system and services running on the server, such as Apache

The configuration details of each machine may be found below.

| Name      | Function | IP Address | Operating System |
|---------- |----------|------------|------------------|
| Jump Box  |Gateway   | 10.0.0.10  | Linux            |
| Web-1     |Web Server| 10.0.0.8   | Linux            |
| Web-2     |Web Server| 10.0.0.9   | Linux            |
| ELK-Server|Elk Server| 10.1.0.10  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
my personal IP address.

Machines within the network can only be accessed by SSH.
JumpBox is the onlyMachine allowed to access my ELK VM and its IP address?_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

 Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because.
The main advantage of automating configuration with Ansible is its very simple to set up and use it lets you model even highly and complex workflows you can as well deploy servers quickly and easily. 

The playbook implements the following tasks:
-Activates ports 5601, 9200, and 5044.
-Installs Docker.io and pip3
-Configures the machine with Docker 
-Downloads and configures ELK docker container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.



![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

 Target Machines & Beats
This ELK server is configured to monitor the following machines:
 List the IP addresses of the machines you are monitoring_
  Web-1 10.0.0.8
  Web-2 10.0.0.9

We have installed the following Beats on these machines:
-Filebeat
-Metricbeat

These Beats allow us to collect the following information from each machine:
-Filebeat watches for log files/locations and collects events related to those files and locations.
-Metricbeat records metrics and statistical data from the operating system and services that are running on the server

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the instal_elk_yml file to your /etc/ansible directory.
- Update the host file to include IP Addresses of Web-1 Web-2 and ELK server also assigning python3 as an interpreter
- Run the playbook, and navigate to ELK to check that the installation worked as expected.

 Answer the following questions to fill in the blanks:_
- Which file is the playbook? Where do you copy it?_/etc/ansible/file/filebeat-configuration.yml
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_edit the /etc/ansible/hosts file to add webserver/elkserver ip addresses
- Which URL do you navigate to in order to check that the ELK server is running?http://[your.ELK-VM.External.IP]:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
