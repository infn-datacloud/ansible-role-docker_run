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
```
env_file: path to file containig a list of environment variables on the form FOO=BAR
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
