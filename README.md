# ELK_Stack-Project
ELK Stack
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

  https://github.com/FreshPescado/ELK_Stack-Project/blob/main/diagrams/ELK_Stack.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

 https://github.com/FreshPescado/ELK_Stack-Project/blob/main/ansible/filebeat-playbook.yml.txt

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting access to the network.

- What aspect of security do load balancers protect?
   A load balancer intelligently distributes traffic from clients across multiple servers without the clients having to understand how many servers are in use or how they are configured. Load Balancing contributes to the Availability aspect of security in regards to the CIA Triad. 

- What is the advantage of a jump box?  
  The advantage of a JumpBox is the orgination point for launching Administrative Tasks. This ultimately sets the JumpBox as a SAW (Secure Admin Workstation). All Administrators when conducting any Administrative Task will be required to connect to the JumpBox (SAW) before perfoming any task/assignment.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.

- What does Filebeat watch for?  
  Filebeat watches for log files/locations and collects log events.
 
- What does Metricbeat record? 
  Metricbeat records metric and statistical data from the operating system and from services running on the server.

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

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- For admin access you can only access the jumpbox and for the dvwa via LB only and ELK only accepts web from home.

Machines within the network can only be accessed by host machine.
- Which machine did you allow to access your ELK VM? 
  Jumpbox 

- What was its IP address? 
  40.77.61.91/dynamic IPV4 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 172.116.233.158      |
| ELK      | No                  | 10.0.0.1-254         |
| Web-1    | No                  | 10.0.0.1-254         |
| Web-2    | No                  | 10.0.0.1-254         |
| Web-3    | No                  | 10.0.0.1-254         |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because
using automated configuration allows for a more accessible environment and allows developers and programmers of multiple skill levels to deploy configurations. It also frees up time which would be spent  configuring ELK and can now be devoted to other more important tasks.

The playbook implements the following tasks:
The playbook implements the following tasks:
Install docker.io
Installs pip3 for python
Install the docker python module
Use sysctl module to increase memory usage
Downloads and launches a docker elk container.

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
- Copy the  file to /etc/ansible.
- update the hosts files to include the IP's of your elk server [10.1.0.4] and the webservers [10.0.05-6] [10.0.0.8] under their respective columns
- Run the playbook, and navigate to http://13.82.212.3:5601/app/kibana to check that the installation worked as expected.
