Ansible role: systemd
=========

![Build & Deploy](https://github.com/Provizanta/ansible-role-systemd/workflows/molecule/badge.svg?branch=master)

Create and setup systemd along with the specified units.

Requirements
------------

None

Role Variables
--------------

These defaults are set in [defaults/main.yml](./defaults/main.yml):

    systemd_units: []   # list of structured unit information

Each unit element is composed of these variables:

    name: <str, unit name>
    type: <enum, service|mount..., unit file extension>
    destination: <enum, primary|secondary|runtime|user, defaults to primary>
    state: <enum, started|stoppped|restarted|reloaded, default started>        # only relevant to services
    enabled: <bool, default true>           # only relevant to services
    masked: <bool, default false>           # only relevant to services
    content: <str, unit file content>

Dependencies
------------

None

Example Playbook
----------------

    - name: Converge
      hosts: all
      roles:
        - role: systemd
          vars:
            systemd_units:
              - name: "test service"
                type: service
                content: |
                  [Unit]
                  Description=Test service

                  [Service]
                  Type=oneshot
                  ExecStart=/bin/echo "Just a test service"
                  RemainAfterExit=yes

License
-------

MIT

Author Information
------------------

Tibor Csóka
