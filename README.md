Role ansible-role-docker_run
=========

The role starts a docker run from images and parameters provided.

Requirements
------------

Docker need to be available in the system. Role suitable for Ubuntu Xsenial (16.04).

Role Variables
--------------

```
appname: name of the container
image: image to be used, default ubuntu
tag: tag for the image to be used, default latest
ports: as from the docker syntax: 8080 or 8080:80, default "80", mandatory
command: command to be executed, can be left blank
```

Environment variables
--------------
Environment variables are supported and passed via TOSCA Template as a list on the form FOO=BAR
Varaible(s) are copied down into a file .env that is used to start the container.
```
env_file: /opt/{{ appname }}/.env  --> path to file containig a list of environment variables on the form FOO=BAR
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
