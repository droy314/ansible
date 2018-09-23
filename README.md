# ansible

My attempt at teaching myself ansible.

# Environment
ansible-control - VirtualBox VM (ubuntu 18.04) running a NAT (with port forwarding) and a Internal network (docker-net).
swarm-manager1 - VirtualBox VM (ubuntu 18.04) running a NAT (no port forwarding) and docker-net (Internal network).

# Traps
* Ubuntu did not get the second network adapter.
    1. Ran `dmesg| grep enp` to get the name of the 2 networks in netplan
    2. In `/etc/netplan/50-cloud-init.yaml` Insert the following (assuming the device name is enp0s8)
      ```
      enp0s8:
         addresses: []
         dhcp4: true
      ```
    3. Run `sudo netplan apply`

    See https://askubuntu.com/a/1043760

* Ansible managed host needs python..Use ansible_python_interpreter variable.
* Add remote user to `/etc/sudoers` without password.
    ```
    <user> ALL=(ALL) NOPASSWD:ALL
    ```
