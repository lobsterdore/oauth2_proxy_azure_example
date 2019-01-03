Vagrant.configure(2) do |config|
  config.vm.network :private_network, ip: "192.168.16.1"
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provision.yml"
  end

end
