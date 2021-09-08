## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](https://github.com/Bayrans/ELK-Server-Setup-Project/blob/main/Images/Network-Diagram-ELK.png "Network Diagram")

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

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

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                 | Function | IP Address | Operating system |
|----------------------|----------|------------|------------------|
| Jump-Box-Provisioner | Gateway  | 10.0.0.4   | Linux            |
| Web-1                | Server   | 10.0.0.5   | Linux            |
| Web-2                | Server   | 10.0.0.6   | Linux            |
| ELK-Server           | Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP address(es): 69.232.248.170


Machines within the network can only be accessed by the Jump-Box-Provisioner (10.0.0.4).
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
it allows for automated deployment to provide quick access to duplicate the results if needed, as well as it can be applied accross multiple machines.

The playbook implements the following tasks:
- Step 1: Install Docker.io - call apt to install the docker engine, docker.io.
- Step 2: Install pip3 - call apt to install Pythons Software, python3-pip
- Step 3: Install Docker Python Client - installs the pip package, docker, required to manage Docker containers for Ansible.
- Step 4: Increase Virtual Memory - uses a command, `sysctl -w vm.max_map_count=262144` to configure the VM to use more memory, required in this case, in order to run the ELK container.
- Step 5: Download and Launch a Docker ELK Container - Downloads the Docker conatainer `sebp/elk:761` with port mappings: 5601:5601 9200:9200 5044::5044, and is prompted to be started.
- Step 6 - Enable Service Docker on boot - uses systemd module on Ansible to enable docker on boot in case a restart is necessary.


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker-ps](https://github.com/Bayrans/ELK-Server-Setup-Project/blob/main/Images/doccker-ps-output.png "docker-ps output")
### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- `Metricbeat` collects metrics on the machine, like CPU and memory usage data.
- `Filebeat` collects log files in specified locations, which can be used for file data  

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the hosts file to include a new group, elk, with the IP address of the machine so it can be called in the hosts field when necessary.
- Run the playbook, and navigate to http://[your.ELK-VM.External.IP]:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
