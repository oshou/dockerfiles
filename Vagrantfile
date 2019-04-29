# -*- mode: ruby -*-
# vi: set ft=ruby :

# Define
VAGRANTFILE_API_VERSION = "2"
VM_BOX = "bento/centos-7.4"
VM_PARAMS = [
  {
    :hostname       => "adm01",
    :private_ip     => "192.168.33.220",
    :shared_source  => "../../../share",
    :shared_target  => "/share"
  },
]

Vagrant.configure(VAGRANTFILE_API_VERSION) { |config|

  config.vm.box = VM_BOX

  VM_PARAMS.each { |vm_param|
    config.vm.define vm_param[:hostname] { |node|
      node.vm.hostname = vm_param[:hostname]
      node.vm.network :private_network, ip: vm_param[:private_ip]
      node.vm.synced_folder vm_param[:shared_source], vm_param[:shared_target], mount_options: ['dmode=777','fmode=777'],owner: 0,group: 0
    }
  }

  # Docker & Git Setup
  config.vm.provision "shell", inline: <<-SHELL
    sudo yum install -y yum-utils
    sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    sudo yum makecache fast
    sudo yum install -y git
    sudo yum install -y docker-ce
    sudo systemctl enable docker
    sudo systemctl start docker
    sudo curl -L https://github.com/docker/compose/releases/download/1.17.1/docker-compose-`uname -s`-`uname -m` > docker-compose
    sudo mv docker-compose /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
    sudo gpasswd -a vagrant docker
    sudo systemctl restart docker
  SHELL
}
