
Setup
=====

```
$ vagrant up
$ ssh `cat ifeth1`
$ sudo apt-get update
$ sudo apt-get upgrade
$ ^D
$ ansible-playbook -v -i ansible/inventory/vagrant-vm ansible/site.yml
$ ssh `cat ifeth1`
$ psql -U postgres
$ ^D
$ curl `cat ifeth1`
```
