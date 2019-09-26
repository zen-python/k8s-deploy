NODES = 1
Vagrant.configure("2") do |config|
    config.ssh.insert_key = false

    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 2
    end

    config.vm.define "k8s-master" do |master|
        master.vm.box = "bento/ubuntu-18.04"
        master.vm.network "private_network", ip: "192.168.10.10"
        master.vm.hostname = "k8s-master"
        master.vm.provision "ansible" do |ansible|
            ansible.playbook = "k8s-setup/master-playbook.yml"
            ansible.extra_vars = {
                node_ip: "192.168.10.10",
            }
        end
    end

    (1..NODES).each do |i|
        config.vm.define "node-#{i}" do |node|
            node.vm.box = "bento/ubuntu-18.04"
            node.vm.network "private_network", ip: "192.168.10.#{i + 10}"
            node.vm.hostname = "k8s-node-#{i}"
            node.vm.provision "ansible" do |ansible|
                ansible.playbook = "k8s-setup/node-playbook.yml"
                ansible.extra_vars = {
                    node_ip: "192.168.10.#{i + 10}",
                }
            end
        end
    end
end
