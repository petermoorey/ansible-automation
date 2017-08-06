# Network automation using Ansible/NAPALM/Jinja2

### playbook-ios-show-cmd-example
Issues a 'show' command to one or more devices and prints output to screen

### playbook-generate-apply-ios-config
Generates configurations for a group of devices and merges or replaces running-config, recording any differences

#### Example of playbook output
Below is the output from the play 'playbook-generate-apply-ios-config'   

```
ubuntu@ansible:~/ansible-lab1$ ansible-playbook playbook-generate-apply-ios-config.yml 

PLAY [Prepare for configuration build] 
****************************************************************************

TASK [file] 
****************************************************************************
ok: [branch1-rtr1 -> localhost]

TASK [file] 
****************************************************************************
ok: [branch1-rtr1 -> localhost]

TASK [file] 
****************************************************************************
ok: [branch1-rtr1]
ok: [branch2-rtr1]
ok: [branch3-rtr1]

PLAY [Generate configs] 
****************************************************************************

TASK [base : Generate configuration files] 
****************************************************************************
ok: [branch3-rtr1]
ok: [branch2-rtr1]
ok: [branch1-rtr1]

PLAY [Assemble configs
****************************************************************************


TASK [assemble] 
****************************************************************************
ok: [branch1-rtr1]
ok: [branch3-rtr1]
ok: [branch2-rtr1]

TASK [apply configs] 
****************************************************************************
ok: [branch2-rtr1]
ok: [branch1-rtr1]
ok: [branch3-rtr1]

PLAY RECAP 
****************************************************************************
branch1-rtr1               : ok=6    changed=0    unreachable=0    failed=0   
branch2-rtr1               : ok=4    changed=0    unreachable=0    failed=0   
branch3-rtr1               : ok=4    changed=0    unreachable=0    failed=0 


```

#### Ansible project file/folder structure
Below is the file structure for the ansible project

* templates folder contains jinja2 (j2) templates used to generate device configurations
* group_vars folder contains common configuration variables referenced in j2 templates
* host_vars folder contains device specific configuration variables referenced in j2 templates
* hosts file contains individual device hostnames and groupings of devices, used as an inventory for SSH/API access
* configs folder contains configurations generated from j2 templates
* logs folder contains configuration differences for each device when applying/validating configs
* playbook* files are YAML files that initiate one or more tasks, like generating and applying configs

```.
├── group_vars
│   └── all.yml
├── hosts
├── host_vars
│   ├── branch1-rtr1
│   ├── branch2-rtr1
│   └── branch3-rtr1
├── playbook-generate-apply-ios-config.yml
├── playbook-ios-show-cmd-example.yml
├── README.md
└── roles
    └── base
        ├── tasks
        │   └── main.yml
        └── templates
            ├── aaa.j2
            ├── base.j2
            ├── dhcp-server.j2
            ├── interfaces.j2
            ├── login-banner.j2
            ├── monitoring.j2
            └── qos.j2
```
