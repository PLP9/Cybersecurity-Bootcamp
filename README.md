# Cybersecurity-Bootcamp
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagramming th Network](/Diagrams/DiagrammingTheNetwork.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Yaml file may be used to install only certain pieces of it, such as Filebeat.

install_elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box? Load balancers protect several aspects of security. One of the ways is by distributing traffic between servers, preventing one server from becoming flooded with requests, which can cause it to malfunction or crash (Dos or DDoS attacks). In this case, a load balancer would protect availability, which is part of the CIA triad.
An advantage of a jump box is that it can help secure remote access to your vm's. 
  

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- What does Filebeat watch for? Filebeat watches for which files have changed and when.
- What does Metricbeat record?_ Metricbeat records metrics and statistics from the system and services running on the server.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.8   | Linux            |
| Web-1    | Webserver| 10.0.0.9   | Linux            |
| Web-2    | Webserver| 10.0.0.10  | Linux            |
| ElkVm    | Webserver| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 98.149.250.101
Machines within the network can only be accessed by the Jump Box.
- Which machine did you allow to access your ELK VM? What was its IP address? Jumpbox machine, IP address: 10.0.0.8

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |  Yes                | 98.149.250.101       |       
| Web-1    |  No                 | 10.0.0.8             |
| Web-2    |  No                 | 10.0.0.8             |
| ElkVm    |  No                 | 10.0.0.8             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? The main advantage of automating configuration with Ansible is that you can create a playbook using Yaml which can 
have a system run multiple tasks. You can also use the same playbook if you have to configure several systems which will be more accurate instead of using a system's gui that can lead to human error.  

The playbook implements the following tasks:
⦁	Installs Docker.io
⦁	Installs python3-pip
⦁	Installs Docker python module
⦁	Increases Virtual memory
⦁	Allows system to use more memory

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Elk Container](/Images/SebpElk-761.JPG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

| Name     |IP Address|
|----------|----------|
| Web-1    |10.0.0.9  |
| Web-2    |10.0.0.10 |



We have installed the following Beats on these machines:
⦁	Filebeat
⦁	Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat collects log data, specifically which files have changed and when.
Metricbeat collects metrics and statistics which help you monitor servers efficiently. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install_elk.yml file to /etc/ansible/.
- Update the hosts file to include the "[elk]Elk Virtual Machine IP address ansible_python_interpreter=/usr/bin/python3 
- Run the playbook, and navigate to "http://[your.ELK-VM.External.IP]:5601/app/kibana" to check that the installation worked as expected.
