Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.synced_folder "./", "/vagrant", type: "virtualbox", create: "true", mount_options: %w[dmode=777 fmode=777]
 
  config.vm.provider "virtualbox" do |vb|
    vb.name   = "etlp"
    vb.memory = 2048
    vb.cpus   = 2
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end
 
  config.vm.define "etlp"
 
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provision/play_book.yml"
  end
end
