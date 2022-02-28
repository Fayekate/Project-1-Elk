## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](https://github.com/Fayekate/Project-1-Elk/blob/main/Diagrams/Project%201%20-%20Elk%20Diagram.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  ### Playbook Files
  
 - [ ] [Elk Playbook](https://github.com/Fayekate/Project-1-Elk/blob/main/Ansible/ansible/elk-Playbook.yml)
 - [ ] [Pentest/DVWA Playbook](https://github.com/Fayekate/Project-1-Elk/blob/main/Ansible/ansible/pentest.yml)
 - [ ] [Filebeat Installation Playbook](https://github.com/Fayekate/Project-1-Elk/blob/main/Ansible/ansible/files/filebeat_installation.yml)
 - [ ] [Metricbeat Installation Playbook](https://github.com/Fayekate/Project-1-Elk/blob/main/Ansible/ansible/files/metricbeat_playbook.yml)
  

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting volnerable to the network.
-What aspect of security do load balancers protect? Availability, Web Traffic, Web Security
-What is the advantage of a jump box?Automation, Security, Network Segmentation, Access Control
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
-What does Filebeat watch for? Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
-What does Metricbeat record? Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.
The configuration details of each machine may be found below. 

| Name          | Function |           IP Address    | Operating System |
|---------------|----------|-------------------------|------------------|
| Jump Box      | Gateway  | 10.0.0.7/20.106.101.91  | Linux            |
| Web-1         | WebServer|  10.0.0.8               | Linux            |                 
| Web-2         | WebServer| 10.0.0.9                | Linux            |                
| Elk           |ELK SErver| 10.1.0.4/20.106.101.91  | Linux            |                

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk Server machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-Workstation Public IP through TCP 5601.

Machines within the network can only be accessed by Workstation and Jump-Box-Provisioner. 
-Which machine did you allow to access your ELK VM? What was its IP address?
-Jump-Box-Provisioner IP : 10.0.0.7 via SSH port 22
-Workstation Public IP via port TCP 5601

A summary of the access policies in place can be found in the table below.

| Name        | Publicly Accessible | Allowed IP Addresses               |
|-------------|---------------------|------------------------------------|
| Jump Box    |     No              | Workstation public IP on ssh 22    |
|  Web1       |     No              | 10.0.0.4 on ssh 22                 |
|  Web2       |     No              | 10.0.0.4 on ssh 22                 |
|Elk server   |     No              |Workstation Public IP usingTCP 5601 |
|Loadbalancer	|     No             	|Workstation Public IP on HTTP 80    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- Specify a different group of machines as well as a different remote user
![](https://github.com/Fayekate/Project-1-Elk/blob/main/Screenshots/Remoteuser-scshots.JPG)  
- Increase System Memory :
![](https://github.com/Fayekate/Project-1-Elk/blob/main/Screenshots/systemmemory-screenshots.JPG) 
- Install the following services:
![](https://github.com/Fayekate/Project-1-Elk/blob/main/Screenshots/dockerio-scshot.JPG)
![](https://github.com/Fayekate/Project-1-Elk/blob/main/Screenshots/pip3-scshot.JPG)
- Launching and Exposing the container with these published ports:
![](https://github.com/Fayekate/Project-1-Elk/blob/main/Screenshots/ports-scshot.JPG)

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1:10.0.0.8
- Web2:10.0.0.9
We have installed the following Beats on these machines:
- ELK Server, Web1 and Web2
- The ELK Stack Installed are: FileBeat and MetricBeat

These Beats allow us to collect the following information from each machine:
- Filebeat: log events
- Metricbeat: metrics and system statistics

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy [] [elk-Playbook.yml](https://github.com/Fayekate/Project-1-Elk/blob/main/Ansible/ansible/elk-Playbook.yml)
- Run the playbook using this command : ansible-playbook install-elk.yml

For FILEBEAT:
- Download Filebeat playbook usng this command:
- curl -L -O https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > /etc/ansible/files/filebeat-config.yml
- Copy the '/etc/ansible/files/filebeat-config.yml' file to '/etc/filebeat/filebeat-playbook.yml'
- Update the filebeat-playbook.yml file to include installer
 - curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.6.1-amd64.deb 
 - Update the filebeat-config.yml file root@c1e0a059c0b0:/etc/ansible/files# nano filebeat-config.yml


Answer the following questions to fill in the blanks:_
- Which file is the playbook? Where do you copy it?For the ANSIBLE : We will create the my-playbook1.yml as our playbook.For FILEBEAT: We will create filbeat-playbook.yml as our playbook.For METRICBEAT: We will create metricbeat-playbook.yml as our playbook.
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?Test Kibana on web : http://[your.ELK-VM.External.IP]:5601/app/kibana
Test Kibana on localhost: sysadmin@10.1.0.4: curl localhost:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
