# Vagrant docker swarm demo

A simple demo of a docker swarm with Vagrant.

## Requirements

Tested with:
- python==3.8.1
- vagrant==2.2.7
- ansible==2.9.6
    - geerlingguy.pip==1.3.0
    - geerlingguy.docker==2.6.0

But there is no reason it should not work with above's other versions.

## preparing 

```sh
$ python -m venv env
$ . env/bin/activate
$ pip install ansible
$ ansible-galaxy install geerlingguy.pip geerlingguy.docker
```

## To change the Number of nodes

Change the value of `N` in `Vagrantfile`.

## Up

```sh 
$ varant up
```

## Apply playbok changes
```sh 
$ vagrant provision # working VMs
# or
$ vagrant up --provision # on precreated VMs
```

