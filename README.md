Ansible provisioning for Symfony3 deployment.

#### Usage ####

```bash
# Clone the repository
$ git clone https://github.com/icamys/ansible-symfony3
$ cd ansible-symfony3

# Edit your inventory
$ vim inventory.yml

# Run the playbook
$ ansible-playbook playbook.yml -i inventory.yml
```

If you are using Vagrant, copy the contents of this repo into a directory called 'provision' add 
following code to Vagrantfile:

```ruby
    symfony_server.vm.provision "ansible_local" do |ansible|
        ansible.verbose           = true
        ansible.install           = true
        ansible.limit             = "all"
        ansible.playbook          = "playbook.yml"
        ansible.inventory_path    = "inventory.yml"
        ansible.provisioning_path = "/vagrant/provisioning"
        ansible.galaxy_role_file  = "requirements.yml"
        ansible.galaxy_roles_path = "roles/"
    end
```