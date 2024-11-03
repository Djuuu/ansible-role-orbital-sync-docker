Ansible Role: Orbital-Sync-docker
=================================

Install Orbital Sync Docker Compose project.

- https://github.com/mattwebbio/orbital-sync

Requirements
------------

Requires the following to be installed:
- docker
- docker compose

It's also assumed you have multiple [Pi-hole](https://pi-hole.net/) instances running.

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
```


Available role variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
# Docker project variables

orbital_sync_project_name: orbital-sync


# Orbital Sync project variables

# mattwebbio/orbital-sync image version
orbital_sync_version: latest

# Primary host configuration is pulled from (inventory hostname)
orbital_sync_primary_pihole:
#  base_url: "https://pihole.example.net"
#  password: "p@55w0rd"

# Secondary hosts configuration is injected into (inventory hostnames)
orbital_sync_secondary_piholes:
#  - base_url: "https://pihole.fallback1.example.net"
#    password: "p@55w0rd1"
#  - base_url: "https://pihole.fallback2.example.net"
#    password: "p@55w0rd2"

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

Pi-hole instances can be installed with:
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
