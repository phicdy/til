## Command

```bash
# launch virtual machine
vagrant up

# stop virtual machine
vagrant halt

# stop and launch virtual machine
vagrant reload

# deploy virtual machine from Vagrantfile
vagrant provision

# create initial Vagrantfile
vagrant init [box]

# list box
vagrant box list

# add box
vagrant box add [box]

# ssh
vagrant ssh
```

### Vagrantfile

```bash
config.vm.box_url = "file://your/local/box/path/centeos.box"

config.vm.synced_folder "local/path/to/sync", "remote/path/to/sync"

config.vm.provider "virtualbox" do |vb|
	vb.gui = true
	vb.memory = "2048"
end

config.vm.provision "ansible_local" do |ansible|
	ansible.playbook = "your_playbook.yml"
	ansible.verbose = "vvv"
end
```

### user

* user:vagrant
* pass:vagrant

### References

* [Vagrantbox.es](http://www.vagrantbox.es/)
* [How do I enable additional debugging output from Ansible and Vagrant?](http://serverfault.com/questions/531891/how-do-i-enable-additional-debugging-output-from-ansible-and-vagrant)
* [Vagrant + Ansible で開発環境を作るなら ansible_local プロビジョナがいい！](http://blog.shin1x1.com/entry/ansible_local-provisioner-in-vagrant)
