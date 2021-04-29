Domain-Join
=========

This role joins a host to my Active Directory domain. This has only been tested in my domain and on Ubuntu machines.

Requirements
------------

This playbook assumes that the host can resolve the domain using DNS. In addition, you need an account with permissions to add computers to the domain.

Role Variables
--------------
Required variables are listed here, along with default example values. See defaults/main.yml. Many of these variables need to be overwritten for the playbook to run. This can be done using the vars role directory, the command line, AWX, etc.

    krb5_default_realm: DOMAIN.COM

The domain the host is joining. This should be resolvable.

    realm_domain: .DOMAIN.COM

This is used to join the domain. This variable is temporary.

    realm_domain_lc: domain.com

The lowercase form of the domain name. This variable is also temporary. 

    krb5_domain_controller: dc01.domain.com

This is the FQDN of the domain controller being queried.

    kerberos_user: admin

This is the user with domain joiner permissions.

    kerberos_user_password: pass

This variable stores the password of the domain joiner account above. I do not recommend storing the password in plain text like this. Instead, use a secure form of storage like an ansible vault encrypted file.

    realm_ad_ou: "OU=Ubuntu,OU=Virtual Machines,OU=Domain Computers,OU=Domain,DC=domain,DC=com"

This is the distinguished name of the OU to join the host to.


    vsphere_datacenter: HomeLab

Example Playbook
----------------

    - name: Join new hosts to the domain.
      hosts: deploy
      become: true
      roles:
        - domain-join

License
-------

BSD

Author Information
------------------

Derek Smiley - Homelabber, Network Analyst, aspiring System Administrator/Ansible Automation Engineer

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/

Much of this was created using snippets from other public repositories on github. I claim ownership of none of this code.