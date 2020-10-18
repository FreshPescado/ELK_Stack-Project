# ELK_Stack-Project
ELK Stack
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

  https://github.com/FreshPescado/ELK_Stack-Project/blob/main/diagrams/ELK_Stack.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  https://github.com/FreshPescado/ELK_Stack-Project/blob/main/ansible/filebeat-playbook.yml.txt

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting access to the network.
- What aspect of security do load balancers protect? A load balancer intelligently distributes traffic from clients across multiple servers without the clients having to understand how many servers are in use or how they are configured. This defends it against DDoS Attacks. What is the advantage of a jump box?  By running your open source apps as JumpBoxes you can work more nimbly and focus your resources on important activities.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.
- What does Filebeat watch for?  Filebeat monitors the log files or locations that you specify.
- What does Metricbeat record? Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web 1    | Server   | 10.0.0.5   | Linux            |
| Web 2    | Server   | 10.0.0.6   | Linux            |
| Web 3    | Server   | 10.0.0.7   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the load balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- For admin access you can only access the jumpbox and for the dvwa via LB only and ELK only accepts web from home.

Machines within the network can only be accessed by host machine.
- Which machine did you allow to access your ELK VM? Jumpbox What was its IP address? 40.77.61.91/dynamic IPV4 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |     No              | 10.0.0.5 10.0.0.6    |
|          |                     | 10.0.0.7             |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? Ansible allows IT administrators to automate away the drudgery from their daily tasks.

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
- name: Install docker.io
  name: Install python3-pip
  name: Install Docker module
  name: download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/FreshPescado/ELK_Stack-Project/blob/main/diagrams/Docker%20PS%20Elk%20VM.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
  10.0.0.6
  10.0.0.7

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, while filebeat monitors the log files or locations that you specify.  

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to /etc/ansible/(mkdirfile_name if you want to).
- Update the hosts file to include webservers: 10.0.0.5 ansible_python_interpreter=/usr/bin/python3
                                               10.0.0.6 ansible_python_interpreter=/usr/bin/python3
                                               10.0.0.7 ansible_python_interpreter=/usr/bin/python3
- Run the playbook, and navigate to each webserver to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? https://github.com/FreshPescado/ELK_Stack-Project/blob/main/ansible Where do you copy it? 
- _Which file do you update to make Ansible run the playbook on a specific machine? hosts file. How do I specify which machine to install the ELK server on versus which to install Filebeat on? added the ELK server to the host file, and specified in YML file that it was installed. 
- _Which URL do you navigate to in order to check that the ELK server is running?  http://[your.VM.IP]:5601/app/kibana.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
