# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  #config.vm.box = "precise64"
  #config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.box = "ubuntu/trusty64"
  config.vm.provider "virtualbox" do |v|
      v.memory = 1024
  end
  # Boot with a GUI so you can see the screen. (Default is headless)
  # config.vm.boot_mode = :gui

  # Assign this VM to a host-only network IP, allowing you to access it
  # via the IP. Host-only networks can talk to the host machine as well as
  # any other machines on the same network, but cannot be accessed (through this
  # network interface) by any external networks.
  # config.vm.network :hostonly, "192.168.33.10"

  # Assign this VM to a bridged network, allowing you to connect directly to a
  # network using the host's network device. This makes the VM appear as another
  # physical device on your network.
  # config.vm.network :bridged

  # Forward a port from the guest to the host, which allows for outside
  # computers to access the VM, whereas host only networking does not.
  config.ssh.forward_agent = true
  #config.ssh.private_key_path = "~/.ssh/id_rsa"
  # For using ssh forwarding you have to set up your system
  # https://help.github.com/articles/using-ssh-agent-forwarding
  config.vm.hostname = "django.dev"
  config.vm.network "private_network", ip: "192.168.50.42"
  config.vm.network :forwarded_port, guest: 80, host: 4241
  config.vm.network :forwarded_port, guest: 8000, host: 4242
  config.vm.network :forwarded_port, guest: 8020, host: 4220
  
  #OSX has bug with nfs
  if (/darwin/ =~ RUBY_PLATFORM) != nil
      config.vm.synced_folder "./src", "/home/vagrant/customer-advocacy", owner: "vagrant", group: "vagrant"
  else
      config.vm.synced_folder "./src", "/home/vagrant/customer-advocacy", type: "nfs", nfs_version:4, owner: "vagrant", group: "vagrant"
  end
  
  # Share an additional folder to the guest VM. The first argument is
  # an identifier, the second is the path on the guest to mount the
  # folder, and the third is the path on the host to the actual folder.
  # config.vm.share_folder "v-data", "/vagrant_data", "../data"

  # Enable provisioning with Puppet stand alone. 
  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "manifests"
    puppet.manifest_file  = "site.pp"
  end
end
