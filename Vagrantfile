Vagrant.configure("2") do |config|
  config.vm.define "maquina1" do |node1|
    node1.vm.box = "ubuntu/focal64"
    node1.vm.network "private_network", ip: "192.168.50.4"
    node1.vm.synced_folder "./ansible", "/ansible"
  
    node1.vm.provider "virtualbox" do |vb|
      vb.name = "maquina1"
      vb.memory = "4024"
      vb.cpus = "4"
    end
  
    node1.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install ansible -y
      ansible-playbook --connection=local /ansible/playbook.yml
    SHELL
  end
  
  config.vm.define "maquina2" do |node2|
    node2.vm.box = "ubuntu/focal64"
    node2.vm.network "private_network", ip: "192.168.50.5"
    node2.vm.synced_folder "./ansible", "/ansible"
  
    node2.vm.provider "virtualbox" do |vb|
      vb.name = "maquina2"
      vb.memory = "4024"
      vb.cpus = "4"
    end
  
    node2.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install ansible -y
      ansible-playbook --connection=local /ansible/playbook2.yml
    SHELL
  end
end
