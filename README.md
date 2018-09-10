Auto installtaion of php (via anyenv) on Mac
===

## Overview

This is a playbook of ansible that enabled auto installtaion of php with anyenv on Mac OS X. In the default setting, the playbook install php 5.6.37.

## Usage on virtual machine (vagrant)

If you use vagrant, you add the box for Mac OS X whose name is "Mac" and vagrant up by the Vagrantfile in this repository.
After that, you just type below command and you can install anyenv, phpenv, php5.6.37.

```
$ vagrant ssh
$ sh provision.sh
```

## Usage not on virtual machin

(1) install ansible

You need to install [ansible (>= 2.0.0)](https://www.ansible.com/).
You can install ansible by the commands below.

```
$ brew update
$ brew install ansible
```

if the error that ruby version is too old occurred , you can fix it below.

```
$ brew install ruby
$ sudo mv /usr/local/bin/ruby /usr/local/bin/ruby2.0.0
$ sudo ln -s /usr/local/Cellar/ruby/2.5.1/bin/ruby /usr/local/bin/ruby
$ brew install ansible
```

(2) Change user name

Change the name of user for /provision/group_vars/all.yml

```
---
user:    "vagrant" 　# change this name into your computer's username.
home_dir: "/Users/{{ user }}"
```

(3) Change the php version you want to install

Change the phpenv_php_version in line 21 on /provision/roles/phpenv/vars/main.yml.

```
phpenv_php_version: 5.6.37  # change here to the version you want
```

(4) provision start

```
$ ansible-playbook -i localhost, -c local provision/playbook.yml
```


















In default, it works on Vagrant if prepare the box of Mac OS X.
