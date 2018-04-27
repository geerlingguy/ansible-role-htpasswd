# Ansible Role: htpasswd

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-ansible.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-ansible)

An Ansible Role that installs `htpasswd` and allows easy configuration of `htpasswd` authentication files (used for HTTP basic authentication with webservers like Apache and Nginx) on Linux-based servers.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    htpasswd_credentials:
      - path: /etc/nginx/passwdfile
        name: johndoe
        password: 'supersecure'
        owner: root
        group: www-data
        mode: 'u+rw,g+r'
    
      - path: /etc/apache2/passwdfile
        name: janedoe
        password: 'supersecure'
        owner: root
        group: www-data
        mode: 'u+rw,g+r'

A list of credentials to be generated (or removed) in the respective files defined by the `path` key for each dict. All parameters except `mode` are required (`mode` defaults to `'u+rw,g+r'` (`0640` in octal)).

## Dependencies

None.

## Example Playbook

    - hosts: servers
    
      vars:
        htpasswd_credentials:
          - path: /etc/nginx/passwdfile
            name: johndoe
            password: 'supersecure'
            owner: root
            group: www-data
            mode: 0640
    
      roles:
        - role: geerlingguy.htpasswd
        - role: geerlingguy.nginx

## License

MIT / BSD

## Author Information

This role was created in 2018 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
