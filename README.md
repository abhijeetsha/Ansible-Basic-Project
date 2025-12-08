# Ansible-Basic-Project
## Installations Of Ansible Package
### Update your system's package list and upgrade installed packages:
  * sudo apt update && sudo apt upgrade -y
### Install the software-properties-common package, which is required to manage repositories:
  * sudo apt install software-properties-common
### Add the official Ansible PPA (Personal Package Archive) to your system to access the latest stable version:
  * sudo add-apt-repository --yes --update ppa:ansible/ansible
### Install Ansible using the apt package manager:
  * sudo apt install ansible -y
### Verify the installation was successful by checking the installed version:
  * ansible --version  
