Ansible Role: Orbital-sync-docker
=================================

Install Orbital Sync Docker Compose project.

- https://github.com/mattwebbio/orbital-sync

Requirements
------------

Requires the following to be installed:
- docker
- docker compose

It's also assumed you have multiple [Pi-hole](https://pi-hole.net/) instances running,
installed with the [djuuu.pihole_docker](https://github.com/Djuuu/ansible-role-pihole-docker) role
(for vars availability).

Role Variables
--------------

Common system variables:

```yaml
timezone: UTC
```

Common Docker projects variables:

```yaml
# Base directory for Docker projects
docker_projects_path: # /var/apps

# Base domain suffix through which Pi-hole instances are accessible internally
local_base_domain: my-host.example.net
```

Required Pi-hole vars for each host:
```yaml
pihole_webpassword:
```

Available role variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
# Docker project variables

orbital_sync_project_name: orbital-sync

# Orbital Sync project variables

# mattwebbio/orbital-sync image version
orbital_sync_version: latest

# Primary host configuration is pulled from (inventory hostname)
orbital_sync_primary_host:
# Primary hosts configuration is injected into (inventory hostnames)
orbital_sync_secondary_hosts: []

# Sync interval
orbital_sync_interval_minutes: 60

# Reject invalid TLS certificates
orbital_sync_tls_reject_unauthorized: 0

# Run only once
orbital_sync_run_once: false
```

Dependencies
------------

This role depends on :
- [djuuu.docker_project](https://github.com/Djuuu/ansible-role-docker-project)

It also supposes Pi-hole instances were installed with:
- [djuuu.pihole_docker](https://github.com/Djuuu/ansible-role-pihole-docker)

Example Playbook
----------------

```yaml
- hosts: all
  gather_facts: false
  roles:
    - djuuu.orbital_sync_docker
```

License
-------

Beerware License
