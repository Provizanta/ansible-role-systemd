Configure systemd unit
=========

Create a systemd configuration unit.

Requirements
------------

None

Role Variables
--------------

    units:
      - name: <unit name>
        type: <unit type, e.g. service, mount...>
        destination: <one of possible destinations: primary (etc), secondary (lib), runtime (run) or user, defaults to primary>
        state: <default started, only relevant to services>
        enabled: <default yes, only relevant to services>
        masked: <default no, only relevant to services>          
        content:
          section:
            directive: value
            another_directive: its_value

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers 
      roles:
       - role: systemd-unit
         vars:
           units: 
             - name: my_service
               type: service
               content:
                 Unit:
                   - Description: service_description
                   - After: network.target

                 Service:
                   - ExecStart: path_to_executable
                     Type: forking
                     PIDFile: path_to_pidfile

                 Install:
                   - WantedBy: default.target

License
-------

MIT

Author Information
------------------

Tibor Csoka
