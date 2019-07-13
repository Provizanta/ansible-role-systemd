Ansible role: systemd
=========

Create and setup systemd along with the specified units.

Requirements
------------

None

Role Variables
--------------

These defaults are set in defaults/main.yml:

    units: []   # list of structured unit information

Each unit element is composed of these variables:

    name: <str, unit name>
    type: <enum, unit type, e.g. service|mount...>
    destination: <enum, primary|secondary|runtime|user, defaults to primary>
    state: <defaut started, only relevant to services>
    enabled: <default yes, only relevant to services>
    masked: <default no, only relevant to services>
    content: <str, unit file content>

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
       - role: systemd
         vars:
           units:
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
