## Getting started

### Install the requisites

| Package    | Download URL                              |
|------------|-------------------------------------------|
| VirtualBox | https://www.virtualbox.org/wiki/Downloads |
| Vagrant    | http://www.vagrantup.com/downloads.html   |

### Start and run the VM's

You can start each of the VM's individually like this:

```sh
vagrant up master
vagrant up app
vagrant up db
```

or you can just start them all up in one command:

```sh
vagrant up
```

Then just remember to accept the minion keys on the master:

```sh
vagrant ssh master
salt-key -A
```
