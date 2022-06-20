Vagrant.configure("2") do |config|

    N = 1

    (1..N).each do |machine_id|

      config.vm.define "machine#{machine_id}" do |machine|

        machine.vm.box =  "almalinux/9.aarch64"
        
#        machine.ssh.insert_key = false
#        machine.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
#        machine.ssh.private_key_path = ["~/.ssh/id_rsa", "~/.vagrant.d/insecure_private_key"]
        machine.vm.hostname = "machine#{machine_id}"
#	      machine.vm.network "forwarded_port", guest: 22, host: "222#{machine_id}"

        machine.vm.provider "parallels" do |prl|
          prl.cpus = "1"
          prl.memory = "512"
          prl.update_guest_tools = true
#          prl.customize ["set", :id, "--adaptive-hypervisor", "on"]
        end

        machine.vm.provision "ansible", playbook: "play.yaml", verbose: "true"

      end

    end

end