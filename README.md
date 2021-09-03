=======
# home_network_configuration
Ansible modules for configuring your home environment

---
Ansible modules to configure components of your home network. When I was setting up my home networking, I wanted to ensure that my home system was categorized as infrastructure as code. These components are some of the modules I developed that could help people during their setup and management of their home network setup.

Variables are currently set with Raspberry Pis in mind for home automation and IOT.

## Modules
1. golden_image: This module allows a user to create a blanket automation to set the standard for all home servers. This one includes setting the SSH key, updating, and configuring the servers.

2. unifi_controller: This module allows the creation of a Unifi Controller similar to a Unifi CloudKey on a Raspberry Pi.

3. bind_9: This module allows the creation of an authoritative Bind 9 DNS for private network resolution. Configuration of the individual forward and reverse zones are required.

## Requirements:

* Installation of Python 3.6+ and PIP.

* Installation of [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html) on your local computer.
This can be completed if the machine `pip install ansible`

* SSH private/public key uploaded to the target servers using this command: `ssh-copy-id -i ~/.ssh/<SSH-KEY.pub> pi@<IP_ADDRESS_OF_TARGET>`
* Enter raspberry password. Default is `raspberry`.

> Example: `ssh-copy-id -i ~/.ssh/id_rsa.pub pi@192.168.200.2`

## Use
1. Clone into your directory of choice using the following command:
`git clone https://github.com/hunttom/home_network_configuration.git`

### To baseline all Raspberry Pi Servers
This playbook updates ensure that Raspberry Pis following standard security practices. Configurations inclue: only accessable via ssh; updates all critical packages via `unattended-upgrades`, installs `vim`, and updates the Raspberry Pi.

1. Update `hosts` file with IP addresses of servers you want to target.
2. Update of all variables
3. Run the command when in the git repository `ansible-playbook baseline_config.yml -i hosts`

### To create Unifi controller
This playbook updates to install the Unifi controller software on a Raspberry Pi.

1. Update `hosts` file with IP addresses of servers you want to target.
    > Note: You can install this on a Raspberry Pi 2 or 3 running Pi Hole. 
2. Update of all variables
3. Run the command when in the git repository `ansible-playbook unifi_config.yml -i hosts`