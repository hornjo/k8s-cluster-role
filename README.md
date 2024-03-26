k8s-installation
=========

Installs a high available k8s cluster with with the option to define a load balancer in front of it.

Requirements
------------

- Kubernetes.core collection
- ansible.posix collection

Role Variables
--------------

    k8s_installation_kubernetes_version: 1.29 # use "1.28" or similar to install the related version
    k8s_installation_network_plugin: calico
    k8s_installation_podnetwork: "192.200.55.0/24"
    k8s_installation_control_plane_endpoint: "10.10.1.120:6443" # LB for kubectl api
    k8s_installation_control_plane_workload: false


Example Playbook
----------------
Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    ---
    - name: Testing the whole Role
      hosts: all
      tasks:
        - name: K8s-installation role
          ansible.builtin.include_role:
            name: k8s-installation
          vars:
            k8s_installation_control_plane_endpoint: "10.10.1.101:6443"
            k8s_installation_kubernetes_version: "1.29"
            k8s_installation_podnetwork: "192.200.55.0/24"
            k8s_installation_control_plane_workload: true

