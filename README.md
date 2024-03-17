Objective
The objective of this project is to develop an Ansible playbook capable of automatically connecting to a target machine from a control machine and deploying required applications while running a static web page. This report provides details on utilizing the Windows Subsystem for Linux (WSL) as the control machine and Oracle VirtualBox with Ubuntu as the target system to deploy the Ansible playbook. The playbook will execute tasks to create a Docker container with an Apache server running a static webpage from a specified subnet.
Infrastructure Setup
Virtual Machine Setup
Control Machine
Windows Subsystem for Linux (WSL) with Ubuntu 22.04 Kernel: WSL allows running a Linux environment on a Windows machine without the need for a separate virtual machine.
Install WSL: wsl --install
Install Ubuntu 22.04: wsl --install -d Ubuntu-22.04
Install Visual Studio Code and add WSL extension for IDE connectivity.
Ansible
Ansible: An open-source automation platform used to manage configuration, application deployment, and task automation.
Install Ansible:
