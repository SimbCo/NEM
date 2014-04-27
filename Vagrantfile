box_name = "precise64"
static_ip = "192.168.111.8"

Vagrant.configure("2") do |config|

    config.vm.box = "#{box_name}"
    config.vm.network :forwarded_port, guest: 3000, host: 3000
    config.vm.network :forwarded_port, guest: 27017, host: 27017
    
    #might we need this for nfs?
    config.vm.network :private_network, ip: "#{static_ip}"
    
    config.vm.provision :ansible do |ansible|
      ansible.playbook = "provisioning/mean.yml"
      ansible.extra_vars = {
        vagrant_static_ip: "#{static_ip}",
        ansible_ssh_user: 'vagrant'
      }
    end
end 
