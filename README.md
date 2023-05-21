# Apach2_Ansible
To configure Apache2 using Ansible, you can follow these steps:

Step 1: Set up an Ansible project

Create a new directory for your Ansible project: mkdir ansible-apache2
Change into the project directory: cd ansible-apache2
Create an Ansible inventory file: touch inventory.ini

[webservers]
192.168.1.100

Step 2: Create an Ansible playbook

Create a playbook file: touch playbook.yml

---
- name: Configure Apache2
  hosts: webservers
  become: true

  tasks:
    - name: Install Apache2
      apt:
        name: apache2
        state: present

    - name: Start Apache2 service
      service:
        name: apache2
        state: started
        enabled: true
        
Run the playbook using the ansible-playbook command:

ansible-playbook -i inventory.ini playbook.yml

Ansible will connect to the target server(s) specified in the inventory file and execute the tasks defined in the playbook.

Ansible will install Apache2 and start the service on the target server.
