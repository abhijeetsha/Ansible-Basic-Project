# Ansible-Basic-Project
## Installations Of Ansible Package
## * Create One Master-Server And Create Three Client-Server.
## * In Maste-Server You Have to Install Ansible Package 
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
### Go TO Host File 
  * sudo vim /etc/ansible/hosts
### In That Host File Add Some Lines Of Client Server
   * Ex 2: A collection of hosts belonging to the 'webservers' group:

   * [servers]
   * server_1 ansible_host=54.146.89.53
   * server_2 ansible_host=18.234.212.135
   * server_3 ansible_host=52.90.59.236
### 
