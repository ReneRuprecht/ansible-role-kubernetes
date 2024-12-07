Role Name
=========

Basic kubernetes ansible role.

Requirements
------------

OS must be (currently) debian based

Role Variables
--------------


# Basic settings
kubernetes_version: "1.31" # sets kubernetes version

kubernetes_is_control_plane: true # is ctrl or worker
kubernetes_ansible_inventory_group: "kubernetes" # specify different groups for your inventory. Can be used to install multiple clusters

kubernetes_kublet_enabled: true 

# network settings

kubernetes_pod_network_cidr: "10.244.0.0/16"

kubernetes_network_config_file_path: >
  https://raw.githubusercontent.com/flannel-io/flannel/master/Documentation/kube-flannel.yml


kubernetes_apiserver_advertise_address: "{{ ansible_default_ipv4.address }}"

Dependencies
------------

The system needs a container runtime (containerd) with systemd.

kubernetes_cgroup_driver: "systemd" can be used to set a cgroup_driver

Example Playbook
----------------

    - hosts: kubernetes
      roles:
         - role: reneruprecht.containerd 
         - role: reneruprecht.kubernetes 

