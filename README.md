# ansible-k8s

Automated deployment of K8S cluster on CentOS

This ansible playbook will help you deploy entire K8S cluster with dependencies on VMware vSphere.

# Steps 

1. git clone https://github.com/waghmaredb/ansible-k8s

2. Edit the k8s-deployment-v1.yml and change below parameters from VARS section

# common environment details
    #ntp_server: <ntp_server_ip>   - Replace <ntp_server_ip> with your NTP server IP/hostname 
    domain: "<DOMAIN NAME>"        - Replace <DOMAINNAME> with your DOMAIN NAME
    dns_server: <DNS SERVER>       - Replace <DNS SERVER> with your DNS server IP/hostname
# vmware environment details
    vcenter_ip: <VCENTER SERVER>   - Replace <VCENTER SERVER> with your vCenter server IP/hostname
    vcenter_username: <USERNAME>   - Replace <USERNAME> with vCenter admin account username
    vcenter_password: <PASSWORD>   - Replace <PASSWORD> with vCenter admin account password
    vmware_datacenter: <DATACENTER>  - Replace <DATACENTER> with VMware datacenter you want to use 
    vmware_cluster: <CLUSTER>      - Replace <CLUSTER> with VMware cluster you want to use
    vm_network: "<VM NETWORK>"     - Replace <VM NETWORK> with VM network you want kubernetes VMs to connect
    k8s_vm_folder: <VMFOLDER>      - Replace <VMFOLDER> with VM folder in which you want to place kubernetes VMs
    k8s_template_name: <K8S TEMPLATE NAME> - Replace <K8S TEMPLATE NAME> with VMware CentOS template name
# K8S environment details
    k8s_master_ip: 192.168.172.100     - Replace IP address with kubernetes master server IP address you want to use
    k8s_network_netmask: 255.255.255.0 - Replace subnet mask with netmask of kubernetes network
    k8s_network_gateway: 192.168.172.1 - Replace gateway with kubernetes network gateway
    k8s_node1_ip: 192.168.172.101      - Repalce IP address with kubernetes node IP address
    #k8s_node2_ip: 192.168.1.102
    #k8s_node3_ip: 192.168.1.103
    #k8s_node4_ip: 192.168.1.104
    #k8s_node5_ip: 192.168.1.105
    #k8s_node6_ip: 192.168.1.106
    #k8s_node7_ip: 192.168.1.107
    #k8s_node8_ip: 192.168.1.108

3. Edit /etc/ansible/hosts file and add below lines at the end. Make sure that you remove leading # and match PI address as per playbook variables 
# [kube_cluster1]
# k8s-master ansible_host=192.168.172.100 ansible_user=root
# worker1 ansible_host=192.168.172.101 ansible_user=root
# worker2 ansible_host=192.168.172.102 ansible_user=root
# worker3 ansible_host=192.168.172.103 ansible_user=root
# worker4 ansible_host=192.168.172.104 ansible_user=root

# [master]
# k8s-master ansible_host=192.168.172.100 ansible_user=root

# [worker]
# worker1 ansible_host=192.168.172.101 ansible_user=root
# worker2 ansible_host=192.168.172.102 ansible_user=root
# worker3 ansible_host=192.168.172.103 ansible_user=root
# worker4 ansible_host=192.168.172.104 ansible_user=root

4. Run k8s-deployment.yml playbook



