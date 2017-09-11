Router
=========

[![Build Status](https://travis-ci.org/rexcze/ansible-role-hassindockeronpi.svg?branch=master)](https://travis-ci.org/rexcze/ansible-role-hassindockeronpi)

This role sets up homeassistant in docker on Raspberry Pi. Tested on Rasperry PI zero wifi.

Requirements
------------

This role requires internet connection, Debian based host system with systemd. So far.

Role Variables
--------------

| Variable                           | Default value          | Comments (type)                                                                      |
| :---                               | :---                   | :---                                                                                 |
| `docker_host_packages`             | `apt-transport-https, ca-certificates, curl, docker.io, gnupg2`| Packages needed to set up docker host        |
| `docker_host_workdir`              | `/opt/hass`            | Working directory on Docker host                                                     |
| `docker_host_docker_enabled`       | `yes`                  | Enable Docker daemon after start                                                     |
| `docker_host_mannge_docker_service`| `True`                 | Manage Docker service on host                                                        | 
| `docker_host_docker_state`         | `started`              | Start docker daemon. If not started all docker command will fail.                    |
| `hass_deploy_config`               | `True`                 | Deploy (True) or not to deploy (False) homeassistant config to /path/config directory|
| `hass_container_name`              | `homeassistant_server` | Docker container name                                                                |
| `hass_image_name`                  | `homeassistant/armhf-homeassistant:latest`| Home assistant Docker image name in Docker registry               |
| `hass_container_state`             | `started`              | Home assistant Docker container state. To be run (started) or not (stopped)          |
| `hass_container_restart_policy`    | `always`               | Home assistant Docker container restart policy (see Ansible or Docker docs)          |
| `hass_image_pull`                  | `True`                 | Pull or not newest docker image from registry                                        |
| `hass_container_listen_port`       | `443`                  | Incoming port to our Home assistant container's default port 8123                    |
| `hass_cfg_*`                        | `config defaults`     | All Home assistant configuration options are in form hass_cfg_variable_name          |

Dependencies
------------

None. Hopefully.

Example Playbook
----------------

    - hosts: raspberries
      roles:
         - { role: rexcze.hassindockeronpi }

License
-------

GPLv3
