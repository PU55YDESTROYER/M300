Vagrant.configure(2) do |config|

    config.vm.define "kari" do |kari|
		kari.vm.box = "ubuntu/xenial64"
		kari.vm.hostname = "kari"
		kari.vm.network "private_network", ip: "10.0.1.10"
			kari.vm.provider "virtualbox" do |vb|
				vb.memory = "512"
				vb.name = "kari"
			end
	end
end