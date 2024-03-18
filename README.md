# Deployment Process using Ansible from control to target machine.

This repository contains an Ansible playbook and necessary files for deploying an Apache HTTP server using Docker containers.

## Infrastructure Setup

### Control Machine

- **Operating System:** Windows Subsystem for Linux (WSL) running Ubuntu 22.04 kernel.
- **Tools Used:** Visual Studio Code with WSL extension.

### Target Machine

- **Operating System:** Ubuntu 22.04 using Oracle VirtualBox.

## Prerequisites

- Ensure control machine WSL installed and configured.
- Install Oracle VirtualBox on your Windows machine.
- Download the Ubuntu 22.04 ISO file from the official Ubuntu website.
- Configure target machine.
- Install openSSH in both target and control machine.

## Installation Steps

1. **Install WSL and Ubuntu 22.04:**
   - Open Command Prompt in Windows 10 as administrator.
   - Run `wsl --install` command and restart your machine.
   - Install Ubuntu 22.04 using `wsl --install -d Ubuntu-22.04` command.

2. **Install Ansible on Control Machine:**
   - Open WSL terminal in Visual Studio Code or Ubuntu terminal.
   - Run the following commands:
     ```
     sudo apt update
     sudo apt install software-properties-common
     sudo add-apt-repository --yes --update ppa:ansible/ansible
     sudo apt install ansible
     ```

3. **Install OpenSSH on Control Machine:**
   - Run the following commands:
     ```
     sudo apt install openssh-client
     sudo apt install openssh-server
     ```

4. **Set Up Target Machine (Ubuntu 22.04):**
   - Install OpenSSH on the Ubuntu virtual machine.
   - Ensure network adapter is set to Bridged Adapter.
   - Obtain the IP address of the target machine using `ifconfig` command.

5. **Verify Connection:**
   - Ping the IP address of the target machine from the WSL terminal.
   - Check connectivity using `sudo ssh user@ip`.

## Ansible Playbook

- Ansible playbook YAML file (`deploy_docker.yml`) is included in this repository.
- Tasks defined in the playbook:
  - Initialize playbook with host as target machine.
  - Install Python package manager (pip) on the target machine.
  - Install Docker Python module using pip.
  - Install Docker on the target machine.
  - Create Docker network.
  - Pull the latest Apache image, expose port 80, and connect volume from the control machine.
  - Copy HTML file from control machine to target machine.

## Deployment

1. **Clone Repository:**
   - Clone this repository to your control machine using `git clone https://github.com/Jeevanandh007/Network-CA1.git` command.

2. **Execute Ansible Playbook:**
   - Run the Ansible playbook from the WSL control machine using Visual Studio Code WSL terminal.

3. **Access Apache Server:**
   - Once the Ansible execution is complete, you can access the deployed Apache server:
     - Load `index.html` with `localhost`.
     - Access it using the subnet IP `172.168.10.2`.

## Files Included

- `deploy_docker.yml`: Ansible playbook YAML file.
- `inventory.txt`: Inventory file for configuring target machine IP with required permissions and login.
- `ansible.cfg`: Ansible configuration file to stop checking Ansible host key.


