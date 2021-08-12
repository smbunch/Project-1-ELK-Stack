# Project-1-ELK-Stack
Cybersecurity Bootcamp Project 1: Cumulative Networking, Cloud Security, ELK Stack product

## Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

Elk-stack-Diagram: ELK_diagram.png
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.
  -filebeat-playbook.yml
  -metricbeat-playbook.yml
This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available in addition to restricting access to the network.
-Load balancers distribute traffic to servers to prevent any one server from being overloaded. This protects against DDoS attacks by preventing servers from being overloaded. The jump box has the advantages of allowing access to the user froma single node, and this means it can be more easily secured and monitored. 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
-Filebeat will monitor log files, collect those events and forward them to the ELK stack. 
-Metricbeat periodically records metric data, including operating system metrics like CPU or memory data related to the services running on the servers. 

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.9   | Linux            |
| VM 1     | DVWA     | 10.0.0.10  | Linux            |
| VM 2     | DVWA     | 10.0.0.11  | Linux            |
| ELK      | Server   |70.37.162.50| Linux            |


### Access Policies
The machines on the internal network are not exposed to the public Internet.
Only the Ansible jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-  99.165.70.246
Machines within the network can only be accessed by SSH.
- The ELK server is accessible from the Ansible jumpbox machine, it's private IP in the network is 10.0.0.9
A summary of the access policies in place can be found in the table below.
| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 |  99.165.70.246       |
| ELK      | No                  |   10.1.0.4           |
| DVWA 1   | No                  |   10.0.0.10          |
| DVWA 2   | No                  |   10.0.0.11          |

### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the automation is is less vulnerable to human error and more efficient, scalable and repeatable.
The playbook implements the following tasks:
- Install docker.
- Install python.
- Install virtual memory.
- Download and launch docker ELK container
- 
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
**Note**: 
Project-1-ELK-Stack/docker_ps_output.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-10.0.0.10
-10.0.0.11
We have installed the following Beats on these machines:
- Filebeat
- Metricbeat
These Beats allow us to collect the following information from each machine:
- Filebeat collects webserver logs and any changes to system files while Metricbeat collects metrics of the operating system including CPU and memory. One example of a Metricbeat log would include any SSH attempts to login while Filebeat would include Apache server logs. _

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:
- Copy the YAML playbook file to the Ansible control node.
- Update the  YAML file to include the IPs, ports and services. 
- Run the playbook, and navigate to container to check that the installation worked as expected.

- The playbook is the YAML file that is located at  /etc/ansible/playbook
- Filebeat will run on the DVWAs, both Virtual machine 1 and virtual machine 2, as will Metricbeat.
-To check that the ELK server is running, navigate to the URL 70.37.162.50:5601, as it runs on that port.

