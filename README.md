# Playbooks and roles for configuring a simple, standalone IdM environment

## Assumptions

### General
- User will have access to 2 VM's with 1G of RAM, 1 cpu and 5G of disk
- The chosen OS will be preinstalled on the VM's
- User will have root access to the Vm's either directly or as the result of sudo
- User will have access to a valid domain or subdomain that can be managed by the IdM server
- User will have access to the repos required to install software
- User on the host machine will need to be either root or a local user on the VM's with sudoers setup for
 <username>        ALL=(ALL)       NOPASSWD: ALL


### OS specific
- Red Hat
-- The base OS should be RHEL 7
-- User will need access to subscribe the systems to RHN or a Satellite

### Role variables found in ./roles/<role_name>/var/main.yml)
- common role 
-- supported_os: (is this deteremined from facts or does it need to be set?)
-- pool: (if you know it)
-- rhn_user: (provide your credentials)
-- rhn_pass:  (provide your credentials)
-- dns_server: 8.8.8.8 (not sure this is a good idea)
-- dns_search: example.local (this won't work very well)
-- rhel_7_base_channels: (predefined)
-- rhel_6_base_channels: (predefined)
-- rhel_5_base_channels: (do we care?)

- ipa-lab role
-- ipa_host: idm.example.local  (should be locally resolvable)
-- ipa_admin: admin (admin user, don't change this)

- ipa-server role
-- ipa_directory_manager_password: Secret123 (will be set during install)
-- ipa_admin_password: Secret123 (will be set during install)
-- ipa_admin_passwd: Secret123 (will be set during install)
-- ipa_realm: EXAMPLE.LOCAL (must be all caps)
-- ipa_domain: example.local (should match above)
-- hostname: "{{ ansible_fqdn }}" (will be determined from facts)
-- ipa_ipaddress: "{{ ansible_default_ipv4.address }}" (ditto)
-- ipa_dns_forwarder: 8.8.8.8 (pound on google)
-- ipa_reverse_zone: 1.168.192.in.addr.arpa (needs to match your local subnet)

- ipa-client role
-- ipaclient_supported_os:
-- ipaclient_server: idm.example.local (needs to be resolvable)
-- ipaclient_domain: idm.example.local (needs to be resolvable)
-- ipaclient_enroll_user: admin
-- ipaclient_enroll_pass: Secret123
-- ipaclient_hostname: "{{ ansible_fqdn }}"
-- ipaclient_force_join: false
-- ipaclient_enable_ntp: true
-- ipaclient_all_ip_addresses: true
-- ipaclient_enable_dns_updates: true

