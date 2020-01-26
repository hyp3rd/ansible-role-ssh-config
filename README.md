Ansible Role SSH Config
=======================

Ansible role allowing to configure, harden, and change the port of an `ssh` server.

Role Variables
--------------

```yaml
---
# defaults file for ssh-config

ssh_config_port: 11260

### hardening
ssh_config_hostkey_List:
  - HostKey /etc/ssh/ssh_host_rsa_key
  - HostKey /etc/ssh/ssh_host_ecdsa_key
  - HostKey /etc/ssh/ssh_host_ed25519_key

# Logging
ssh_config_loglevel: VERBOSE
ssh_config_logfacility: AUTHPRIV

# Authentication
ssh_config_permitrootlogin: "no"
ssh_config_strictmodes: "yes"
ssh_config_maxauthtries: 2
ssh_config_maxsessions: 2

ssh_config_permitemptypasswords: "no"
ssh_config_passwordauthentication: "no"

ssh_config_challengeresponseauthentication: "no"

ssh_config_usepam: "yes"

ssh_config_allowagentforwarding: "no"
ssh_config_allowtcpforwarding: "no"

ssh_config_x11forwarding: "no"

ssh_config_tcpkeepalive: "no"
ssh_config_compression: "no"
ssh_config_clientalivecountmax: 2
ssh_config_usedns: "no"
ssh_config_permittunnel: "no"
```

Example Playbook
----------------

```yaml
- hosts:
    - all
  become: True
  gather_facts: True

  roles:
    - role: ansible-role-ssh-config
      ssh_config_port: 11122
      ssh_config_maxauthtries: 2
      ssh_config_maxsessions: 2
      ssh_config_passwordauthentication: "yes"
```

Test
----

The testing environment leverages [molecule](https://molecule.readthedocs.io/en/stable/index.html).
To run all the tests, after installing the `molecule` requirements, execute the following command in a terminal:

```bash
molecule test
```

or

```bash
chmod +x run-tests.bash && ./run-tests.bash
```

License
-------

[BSD-2-Clause](./LICENSE)

Author Information
------------------

[Francesco Cosentino](https://www.linkedin.com/in/francesco-cosentino/)

I'm a surfer, a crypto trader, and a DevSecOps Engineer with 15 years of experience designing highly-available distributed production environments and developing cloud-native apps in public and private clouds.
