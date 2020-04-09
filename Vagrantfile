N = 3

Vagrant.configure("2") do |config|  
  config.vm.box = "ubuntu/bionic64"
  (1..N).each do |node_id|
    config.vm.define "node#{node_id}" do |node|
      node.vm.hostname = "node#{node_id}"
      node.vm.network "private_network", ip: "192.168.50.#{20+node_id}"
      if node_id == N
        node.vm.provision :ansible do |ansible|
          ansible.limit = "all"
          ansible.groups = {
              "managers" => ["node1"],
              "workers" => ["node[2:#{N}]"], # 03, 04...
              "docker:children" => ["managers", "workers"],
              "docker:vars" =>{
                "swarm_init_interface" => "enp0s8"
              }
          }
          ansible.playbook = "swarm.yaml"
        end
      end
    end
  end
end
