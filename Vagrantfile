#  -*-  mode:  ruby -*-
# vi: set ft=ruby  :

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION)  do  |config|
  # General Vagrant VM   configuration.
  config.vm.box  =  "centos/7"
  config.ssh.insert_key  =  false
  config.vm.synced_folder  ".",  "/vagrant",  disabled:  true

  #  ControlMaster
  config.vm.define  "worker"  do  |app|
    app.vm.hostname  =  "worker"
    #app.vm.provider  :virtualbox  do  |v|
    #    v.memory  =  4092
    #end
    app.vm.network  :private_network,  ip:  "192.168.60.100"
  end

end
