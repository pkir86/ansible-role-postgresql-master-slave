Vagrant.configure("2") do |config|
config.vm.box = "centos/7"
config.vm.provider :virtualbox do |v|
v.memory = 2048
end
config.vm.define "centosvm1" do |centosvm1|
  centosvm1.vm.hostname = "centos7vm1.test"
  centosvm1.vm.network :private_network, ip: "192.168.99.24"
  centosvm1.vm.network :private_network, ip: "192.168.98.24"
end
config.ssh.insert_key = false
config.ssh.private_key_path="~/.vagrant.d/insecure_private_key"
end

Vagrant.configure("2") do |config|
config.vm.box = "centos/7"
config.vm.provider :virtualbox do |v|
v.memory = 2048
end
config.vm.define "centosvm2" do |centosvm2|
  centosvm2.vm.hostname = "centos7vm2.test"
  centosvm2.vm.network :private_network, ip: "192.168.99.25"
  centosvm2.vm.network :private_network, ip: "192.168.98.25"
end
config.ssh.insert_key = false
config.ssh.private_key_path="~/.vagrant.d/insecure_private_key"
end
