# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  if (/cygwin|mswin|mingw|bccwin|wince|emx/ =~ RUBY_PLATFORM) != nil
    config.vm.synced_folder ".", "/vagrant", mount_options: ["dmode=700,fmode=600"]
  else
    config.vm.synced_folder ".", "/vagrant"
  end
  config.vm.define "maasdev" do |d|
    d.vm.box ="ubuntu/trusty64"
    d.vm.hostname = "maasdev"
    d.vm.network "forwarded_port", guest: 27017, host: 27017
    d.vm.network "forwarded_port", guest: 3306, host: 3306
    d.vm.network "forwarded_port", guest: 9000, host: 9000
    d.vm.provision :shell, path: "scripts/bootstrap4Ubuntu_ansible.sh"
    d.vm.provision :shell, inline: "PYTHONUNBUFFERED=1 ansible-playbook /vagrant/ansible/maas.yml -c local"
<<<<<<< HEAD
=======
   # d.vm.provision :shell, inline: "PYTHONUNBUFFERED=1 ansible-playbook /vagrant/ansible/mongodb.yml -c local"
>>>>>>> ca3590bc46ec70c2df896758416ce6e29fff0e1c
    d.vm.provider "virtualbox" do |v|
      v.memory = 2048
    end
  end
  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end
end
