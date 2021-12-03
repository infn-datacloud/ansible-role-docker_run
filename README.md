Role docker_run
=========

The role starts a docker container from the specified image and parameters.

Requirements
------------

Docker needs to be available in the system. This requirement is managed via indigo-dc.docker dependency)  

Role Variables
--------------


- `docker_run_appname`: name of the container
- `docker_run_image`: image to be used. Default: ubuntu
- `docker_run_tag`: tag for the image to be used. Default: latest
- `docker_run_env_variables`: list of environment variables (key/value pair) - see below. Default: [] 
- `docker_run_ports`: list of ports to publish from the container to the host. Use the docker CLI syntax, e.g. [ "8080" ] or [ "8080:80" ].  Default: []
- `docker_run_command`: command to be executed, can be left blank


Environment variables
--------------
Environment variables are supported and passed as a list of key/value pairs.
Varaible(s) are copied down into a file .env that is used to start the container.
```
env_file: /opt/{{ docker_run_appname }}/.env  --> path to file containig a list of environment variables in the form FOO=BAR
```

Dependencies
------------

- indigo-dc.docker

Example Playbook
----------------

```
- hosts: localhost
  remote_user: root
  roles:
    - role: ansible-role-docker_run
      docker_run_appname: nginx
      docker_run_image: nginx
      docker_run_tag: latest
      docker_run_ports: [ "8080:80" ] 
      docker_run_command: ""
```


License
-------

BSD

Author Information
------------------

Alessandro Costantini (INFN-CNAF), to continue the work of Diego Ciangottini (INFN-PG)
