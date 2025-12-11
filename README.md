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
   * server_1 ansible_host=54.146.89.53 <ip_add>
   * server_2 ansible_host=18.234.212.135 <ip_add>
   * server_3 ansible_host=52.90.59.236 <ip_add>
   
### Copy your keys From local server to master server Command is:
  * scp -i "Ansible-key.pem" Ansible-key.pem ubuntu@ec2-54-163-216-228.compute-1.amazonaws.com:/home/ubuntu/keys
### Again go to /etc/ansible/hosts file and add some line
  * [servers:vars]
  * ansible_python_interpreter=/usr/bin/python3
  * ansbile_user=ubuntu
  * ansible_ssh_private_key_file=/home/ubuntu/keys/ansible-master-key.pem
### Give Permisions to private key
  * sudo chmod 400 /home/ubuntu/keys/ansible-master-key.pem
### Not connected Run this Command:
  * You Directly enter into the server and handel it all resource
  * ssh -i /home/ubuntu/keys/ansible-master-key.pem ubuntu@50.17.116.251
### For Checking ping master server to client server command is:
  * ansible servers -m ping
### For Updating All servers command is:
  * ansible servers -a "sudo apt update"
### Project1:-
### Install Nginx File with Playbook
  * File name: install-nginx.yaml
  * Code:
  * -
      name: Install Nginx and Start It
      hosts: all
      become: yes
     tasks:
       - name: Insall Nginx
          apt:
          name: nginx
          state: latest
       - name: Start Nginx
          service:
          name: nginx
          state: started
          enabled: yes
 * Run Command: ansible-playbook install-nginx.yaml
### Project2:- Deplyo static webpage hosting on Prodcution server
  * File name: deploy-static-webpage.yaml
  * Code:
  -
    name: Install Nginx and server static website
    hosts: prod
    become: yes
    tasks:
      - name: Install Nginx
        apt:
          name: nginx
          state: latest

      - name: Start nginx
        service:
          name: nginx
          state: started
          enabled: yes

     - name: Deploy Web Page
        copy:
          src: index.html
          dest: /var/www/html/
  * Create index.html add html code and
  * ansible-playbook deploy-static-webpage.yaml
  * Go to browser and check with your public IP.
