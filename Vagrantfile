# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "centos-6.4-x86_64_nrel_puppet"
  config.vm.box_url = "http://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.4-x86_64-v20131103.box"

  # configure the proxies using https://github.com/tmatilai/vagrant-proxyconf
  # substitute your proxy gateway and omissions below.
  if Vagrant.has_plugin?("vagrant-proxyconf")
    config.proxy.http     = "http://10.10.2.100:3128/"
    config.proxy.https    = "http://10.10.2.100:3128/"
    config.proxy.no_proxy = "localhost,127.0.0.1, 192.168.33.*, 192.168.56.*, 10.10.102.*"
  end

  config.vm.hostname = "vagrantcentos64.example.com"

  config.vm.network :private_network, ip: "192.168.33.20"

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "puppet/manifests"
    puppet.module_path = "puppet/modules"
    puppet.manifest_file  = "site.pp"
    puppet.options = "--verbose"
  end

end