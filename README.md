Role docker_run
=========

The role starts a docker container from the specified image and parameters.

Requirements
------------

Docker need to be available in the system. 

Role Variables
--------------

```
appname: name of the container
image: image to be used, default ubuntu
tag: tag for the image to be used, default latest
ports: list of ports in the docker syntax, e.g. [ "8080" ] or [ "8080:80" ], default [ "80" ], mandatory
command: command to be executed, can be left blank
```

Environment variables
--------------
Environment variables are supported and passed as a list of key/value pairs.
Varaible(s) are copied down into a file .env that is used to start the container.
```
env_file: /opt/{{ appname }}/.env  --> path to file containig a list of environment variables in the form FOO=BAR
```

Dependencies
------------

None

Example Playbook
----------------

```
- hosts: localhost
  remote_user: root
  roles:
    - role: ansible-role-docker_run
      appname: container
      image: ubuntu
      tag: latest
      ports: "80" 
      command: "printenv"
```


License
-------

BSD

Author Information
------------------

Alessandro Costantini (INFN-CNAF), to continue the work of Diego Ciangottini (INFN-PG)
