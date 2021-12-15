# ELK-Stack-Project
Project 1 
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

-elkdiagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

- install-elk.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _available____, in addition to restricting _access____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_ Load balnacers are a important role in security because the off-loading function of a load balancer defends a company against a DDOS attack by shifting trafffic from a corprate server to a public cloud server.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _data____ and system __Logs___.
- _TODO: What does Filebeat watch for? Filebeat watches for log files or locations 
- _TODO: What does Metricbeat record? Metricbeat helps to monitor servers watches for system and services running on the server. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function       | IP Address | Operating System |
|----------|----------------|------------|------------------|
| Jump Box | Gateway        | 10.0.0.4   | Linux            |
| Web1     | VM             | 10.0.0.5   | Linux            |
| Web2     | VM             | 10.0.0.7   | Linux            |
| Web3     | VM             | 10.0.0.9   | Linux            |
| Elk      | Elk container  | 10.1.0.4   | Linux
            data collection

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- : 20.124.184.135 |Whitelisted IP addresses_ | 10.0.0.5 | 10.0.0.7| 10.0.0.9 |

Machines within the network can only be accessed by ___ip__.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ i gave access to my main PC ( 20.124.184.135)

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
| Web1     | No                  | 10.0.0.5             |
| Web2     | No                  | 10.0.0.7             |
| Web3     | No                  | 10.0.0.9             |
| Elk      | Yes                 | 10.1.0.4             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible? 
      The main advantage that you get for automating configurations with elk are you do not have to type each command to start a application, so with ansible once you start the machine it runs teh commands or scripts that are in said playbook.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- install docker and ansible on the jumpbox, enable the playbooks automation to move all the software services to the other VMs.
- add the elk VM to the hosts file 
- run the playbooks using the ansible-playbook command, moving task to other machines assigned to receive task  
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring - the web VMs are being monitored 10.0.0.5, 10.0.0.7
10.0.0.9
We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed- Firebeat, Metricbeat 

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
 it keeps track of access if something happened to any sensitive filies it will be much easier to loacate and resolve the issue. Metricbeat monitors usage like CPU, memory also looks at any traffic coming in or out.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _elk_install yml____ file to _/etc/ansible/roles____.
- Update the __hosts___ file to include the destination IP of the elk server
- Run the playbook, and navigate to http://[your_elk_server_ip]:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ - .yml files are playbook files, these files are copied to containers 
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_  hosts file allows for grouping to dictate where rescources go.  
- _Which URL do you navigate to in order to check that the ELK server is running? - [VM_Public_IP:5601/app/kibana]

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._ 
