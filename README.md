## Building Kubernetes(k8s) cluster on Ubuntu server with Ansible

Define inventory in __hosts__ file for clusters
```
[masters]
master ansible_host=192.168.0.7 ansible_user=vagrant

[workers]
worker1 ansible_host=192.168.0.11 ansible_user=vagrant
worker2 ansible_host=192.168.0.12 ansible_user=vagrant

[all:vars]
ansible_python_interpreter=/usr/bin/python3
```

Create user for ansible as defined in __initial.yml__ file
```bash
ansible-playbook -i hosts initial.yml
```

Install dependencies for setting up k8s cluster
```bash
ansible-playbook -i hosts k8s-dependencies.yml
```

Set up and initial k8s on master machine
```bash
ansible-playbook -i hosts master.yml
```

Join all workers machine to k8s cluster
```bash
ansible-playbook -i hosts workers.yml
```
