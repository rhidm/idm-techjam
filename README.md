# Playbooks and roles for configuring a simple, standalone IdM environment

## Assumptions

### General
- User will have access to 2 VM's with 1G of RAM, 1 cpu and 5G of disk
- The chosen OS will be preinstalled on the VM's
- User will have root access to the Vm's either directly or as the result of sudo
- User will have access to a valid domain or subdomain that can be managed by the IdM server
- User will have access to the repos required to install software

### OS specific
- Red Hat
-- The base OS should be RHEL 7
-- User will need access to subscribe the systems to RHN or a Satellite


