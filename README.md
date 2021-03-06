# project-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](Diagram_1.drawio.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible.cfg file may be used to install only certain pieces of it, such as Filebeat.

  ![](project-1/ansible_files/ansible.cfg.pdf)
  https://docs.google.com/document/d/1o_F1MWFGQSn1YRw8oQgXuH-x2T76SyKpsUTkxxBKQrw/edit?usp=sharing

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly protected from a DDos attack, in addition to restricting high traffic to the network.
- * What aspect of security do load balancers protect? What is the advantage of a jump box? Load balancers protect from a DDoS attack by distributing traffic in a balanced way. A jump box will allow us access to all our VM's from one device, can facilitate management of other VM's, and gives secure access.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- * What does Filebeat watch for?_
- Filebeat watches log files, as well as log events. 
- * What does Metricbeat record?_ Metricbeat records metrics and statistics from an operating system. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function   | IP Address | Operating System |
|-----------|------------|------------|------------------|
| Jump Box  | Gateway    | 10.0.0.4   | Linux            |
| web-1     |     server | 10.0.0.5   | Linux            |
| web-2     |   server   | 10.0.0.6   | Linux            |
|VM1-for-elk| Server     | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 99.120.148.234

Machines within the network can only be accessed by Jumpbox 23.96.39.81.
A summary of the access policies in place can be found in the table below.

| Name         | Publicly Accessible | Allowed IP Addresses |
|--------------|---------------------|----------------------|
| Jump Box     | Yes                 | local machines ip    |
|  web-1       |   no                |  10.0.0.4            |
|  web-2       |   no                |       10.0.0.4       |
|  VM1-for-elk |   no                |   10.0.0.4           |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
*There could be more errors when doing configurations manually,so we were able to decrease errors,and save time configuring all the machines with ansible han doing each manually.

The playbook implements the following tasks:
- * In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- install docker.io
- install python3.pip
- install docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


![](Images/project1-day1-docksnap.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
_ web-1:10.0.0.5 web_2:10.0.0.6 web-3:10.0.0.7

We have installed the following Beats on these machines:
- Filebeat and Metricbeat


These Beats allow us to collect the following information from each machine:
 Filebeat collects log files from the machines. For each log it makes a harvester.
 Example of filebeat:
 ![](examplefilebeat.PNG)
- Metricbeat collects system and application metrics. Example:
![](Examplemetricbeat.PNG)

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include the ip address 
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

* Answer the following questions to fill in the blanks:_
-Which file is the playbook? Where do you copy it? filebeat-playbook.yml is the playbook, can be copied in etc/ansible/files/filebeat-playbook.yml
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ Update hosts file in etc/ansible/hosts , add elk server by adding in webserver the elkservers ip address.
- _Which URL do you navigate to in order to check that the ELK server is running?
- http://[publicip:5601]/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
