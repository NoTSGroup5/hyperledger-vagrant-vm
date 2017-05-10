Vagrant.configure(2) do |config|

    config.vm.define "hyperledger" do |hyperledger|
        # Base template for virtualbox, we use ubuntu 14.04 here
        hyperledger.vm.box = "ubuntu/xenial64"
        # Domain on which our application will respond later on
        hyperledger.vm.hostname  = "hyperledger.dev"
        # IP address will be used by the VM
        hyperledger.vm.network :private_network, ip: "192.168.33.151"

        # Tell vagrant to run ansible as a provisioner
        hyperledger.vm.provision :ansible do |ansible|
            # where the playbook is located
            ansible.playbook = "provisioning/playbook.yml"
        end
    end

    # Access the shared vagrant directory via NFS, otherwise slow on mac and windows
    config.vm.synced_folder ".", "/vagrant", type: "nfs"

    config.vm.provider "virtualbox" do |v|
        # tell virtualbox to give our machine 1 GB RAM and 2 Cores
        v.memory = 2048
        v.cpus = 2
    end
end
