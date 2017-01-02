# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "hydrarulz/laravel-development"

  # If you host the box on a remote url
  # config.vm.box_url = ""
  config.ssh.username = "ubuntu"

  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 8000, host: 8000

  # Setup a bridged adapter
  config.vm.network :public_network

  # Share the default directory
  config.vm.synced_folder '.', '/vagrant'

  config.vm.provider "virtualbox" do |vb|
    host = RbConfig::CONFIG['host_os']

    # Give VM 1/4 system memory
    if host =~ /darwin/
        # sysctl returns Bytes and we need to convert to MB
        mem = `sysctl -n hw.memsize`.to_i / 1024
        elsif host =~ /linux/
        # meminfo shows KB and we need to convert to MB
        mem = `grep 'MemTotal' /proc/meminfo | sed -e 's/MemTotal://' -e 's/ kB//'`.to_i
        elsif host =~ /mswin|mingw|cygwin/
        # Windows code via https://github.com/rdsubhas/vagrant-faster
        mem = `wmic computersystem Get TotalPhysicalMemory`.split[1].to_i / 1024
    end
    mem = mem / 1024 / 4
    vb.customize ["modifyvm", :id, "--memory", mem]

    # Set the log file
    vb.customize ["modifyvm", :id, "--uartmode1", "file", "./hydrarulz-laravel-development.log" ]
  end

end
