# Network automation using Ansible/NAPALM/Jinja2

### playbook-ios-show-cmd-example
Issues a 'show' command to one or more devices and prints output to screen

### playbook-generate-apply-ios-config
Generates configurations for a group of devices and merges or replaces running-config, recording any differences

#### Example of playbook output
Below is the output from the play 'playbook-generate-apply-ios-config'   

```
ubuntu@ansible:~/ansible-lab1$ ansible-playbook playbook-generate-apply-ios-config.yml 


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

```

```
