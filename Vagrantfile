Vagrant.configure("2") do |config|

	config.vm.define "controller" do |controller|
		controller.vm.box = "geerlingguy/centos7"
		controller.vm.provider "virtualbox" do |vb|
			vb.memory = 2048
			vb.cpus = 2
		end
		controller.vm.hostname = "ansible-controller"
		controller.vm.network "public_network"
		controller.vm.synced_folder "controller/", "/controller"
		controller.vm.provision "ansible_local" do |ansible|
			ansible.playbook = "playbooks/controller.yml"
		end
	end
	
	config.vm.define "guest" do |guest|
		guest.vm.box = "geerlingguy/centos7"
		guest.vm.provider "virtualbox" do |vb|
			vb.memory = 2048
			vb.cpus = 2
		end
		guest.vm.hostname = "guest"
		guest.vm.network "public_network"
	    guest.vm.synced_folder "guest/", "/guest"
		guest.vm.provision "ansible_local" do |ansible|
			ansible.playbook = "playbooks/guest.yml"
		end
	end	
end