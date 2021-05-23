## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._


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
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box? 

•	The jump box serves as a gateway between all the VM’s and act as a front-line when connecting to the internet. The jump box reduce potential attacks surface by giving access control to a single strong access point rather than many individual VM’s.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.

- _TODO: What does Filebeat watch for? 
Filebeat monitors log files or locations that you specify, collects that log events then forwards it to either Elasticsearch or Logstash for indexing.

- _TODO: What does Metricbeat record?
Metricbeat collects metrics from the operating system and from services running on the server, then takes the metrics and statistics that it collects and send them to the output you specify. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table.

| Name     | Function  | IP Address | Operating System |
|----------|---------- |------------|------------------|
| Jump-Box | Gateway   | 10.1.0.4   | Linux            |
| Web-1    | Container | 10.1.0.5   | Linux            |
| Web-2    | Container | 10.1.0.6   | Linux            |
| Web-3    | Container | 10.1.0.7   | Linux            |
| ELK-VM   | Container | 10.2.0.5   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the host machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

•	168.62.56.78

Machines within the network can only be accessed by SSH and HTTP via the jump-box.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? 

•	You can access the ELK VM by using ip 52.229.49.69 and jump box 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses  |
|----------  |---------------------|---------------------- |
| Jump Box   | Yes                 | 168.62.56.78, 10.1.0.4|
| Web-1      | No                  |10.1.0.5               |
| Web-2      | No                  |10.1.0.6               |
| Web-3      | No                  |10.1.0.7               |
| ELK-VM     | Yes                 |52.229.49.69, 10.2.0.5 |
| Red-Team-LB| Yes                 |20.185.219.214         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
  
•	It allows for Continuous Integration and Continuous Deployment

The playbook implements the following tasks:

•	Installs Docker
•	Download images
•	Downloads and Launches Docker ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

 

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

•	10.1.0.5
•	10.1.0.6
•	10.1.0.7

We have installed the following Beats on these machines:

•	Filebeats
•	Metricbeats

These Beats allow us to collect the following information from each machine:

•	Filebeat collect log data from the VM’s and allows us to monitor and changes that take places. 
•	Metricbeat monitors and collect the system metrics such as uptime and memory usages.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

•	Copy the filebeat-playbook.yml file to /etc/ansible/roles.
•	Update the /etc/ansible/hosts file to include [webservers] and their correlating IP addresses, along with [elk] and it’s IP address.
•	Run the playbook, and navigate to http://ELKpublicIPaddress:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
 
_Which file is the playbook? Where do you copy it?

•	Copy /etc/ansible/files/filebeat-config.yml to /etc/filebeat/filebeat.yml

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
You update the filebeat-config.yml. You then update the host files with the IP addresses of the [webservers] and [elkservers].

- _Which URL do you navigate to in order to check that the ELK server is running?

•	http://[public_IP_ELK]:5601/app/kibana



