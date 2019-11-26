# ansible-k8s

Automated deployment of K8S cluster on CentOS

These ansible playbooks will help you deploy entire K8S cluster with dependencies on VMware vSphere

There are multiple files in this repo. 

1. dependencies.yml
   This playbook needs to be executed on all K8S nodes (master and worker)

2. hosts
   Enter the K8S environment IP and hostname details which you're planning to use
   
3. k8s-esxi-vm-creation.yml
   This playbook is for creating required VMs using existing templates. Need to edit this file to match your tempalte details, networking details, etc. Please go through the comments in the file
   
4. master.yml
   This playbook is only for K8S master. This playbook will configure K8S cluster and install Flannel for pod networking
   
5. vmware-env.yml
   This YML file contains VMware environment details which will be parsed during VM creation. Please go through the note and make required chages to match your environment   
   
6. workers.yml
   This playbook is only for K8S worker nodes. This playbook will join the worker nodes in K8S cluster.


# Steps 

1. Edit the hosts file and enter K8S cluster details (IP address and hostnames)
2. Edit the vmware-env.yml and make sure VMware environment parameters are matching your VMware setup
3. Edit k8s-esxi-vm-creation.yml file and make sure VM placement and networking details are updated
4. Run the k8s-esxi-vm-creation.yml playbook
5. Run the dependencies.yml playbook
6. Run the master.yml playbook
7. Run the workers.yml playbook



