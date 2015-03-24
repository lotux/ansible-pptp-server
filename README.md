# PPTP VPN

Configure PPTP server on CentOS 7.

Prerequisites:

- EPEL (?)
- Ansible

group_vars/all.yml consists these variables:

    pptp_users:
      user1:
        password: password1
      user2:
        password: password2

    pool_first_octets: 192.168.1
    routing_subnet_1: 192.168.100.0/24
    routing_subnet_2: 172.31.0.0/16

- pool_first_octets - pool for clients
- routing_subnet_1, routing_subnet_2 - inject dynamic routes

group_vars/all.yml is encrypted file.

    $ ansible-vault create
    $ ansible-vault encrypt group_vars/all.yml --vault-password-file ~/.ansible_vault_pass.txt
    $ ansible-vault edit group_vars/all.yml --vault-password-file ~/.ansible_vault_pass.txt

Run playbook:

    $ ansible-playbook site.yml -i "server," --vault-password-file ~/.ansible_fly_vault_pass.txt

