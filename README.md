## Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.
![Diagram](https://github.com/Meroneafuwork/Main-repository/blob/main/Diagram/Cloud%20Security%20and%20Virtualization%20Homework.drawio.png)
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml file may be used to install only certain pieces of it, such as Filebeat.
[Filebeat](https://github.com/Meroneafuwork/Main-repository/tree/main/Ansible/filebeat)
This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build
### Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly reliable, in addition to restricting attacks to the network.
- Load balacers, if working accurately, will balance load between the 2 servers and blocks ARP spoofing that will prevent a potential DDOS attack.The advantage of a jump box is that the enviornment we are creating is secure with restricted access using network security group plus an ssh key to create a secure connection with the host machine and the jump box, which then makes it hard for hackers to reach the servers.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
-Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing
- Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server.
- The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  |  10.0.0.4  | Linux            |
| Web-1    |  server  |  10.0.0.5  | Linux            |
| Web-2    |  server  |  10.0.0.6  | Linux            |
| ELK      |  monitor |  10.1.0.4  | Linux            |
### Access Policies
The machines on the internal network are not exposed to the public Internet. 
Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 73.12.7.39
- Machines within the network can only be accessed by private IP address.
- The Jump box machine is allowed to access the ELK VM and the IP address is 10.0.0.4
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.4             |
| ELK      | Yes                 | 13.70.155.137        |
### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because time was saved and minor errors were avoided.
- The advantage of automating configuration with ansible is that the ELK machine was configured using a single command as compaired to going into all the VM and running a manual configuration. This saves time and money. 
The playbook implements the following tasks:
-It first installs docker.io along side with python3-pip. 
-Installs docker python module, then sets the vm.max_count to 262144 in sysctl. 
-The Elk web container is then downloaded and launched using the specific ports. Finally docker service is enabled.
### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 :- 10.0.0.5 and Web-2 :- 10.0.0.6
We have installed the following Beats on these machines:
- Filebeat and Metrixbeat
These Beats allow us to collect the following information from each machine:
- -Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing
- Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
SSH into the control node and follow the steps below:
- Copy the playbook.yml file to ansible directort which is located in /etc/ansible.
- Update the hosts file to include the private IP addresses of Web-1 , Web-2 and ELK
- Run the playbook, and navigate to ELK servers public IP through kibana to check that the installation worked as expected.
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
-sudo apt update, sudo apt upgrade, sudo install docker.io, sudo apt install phython3.pip etc..









