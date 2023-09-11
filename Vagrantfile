Vagrant.configure("2") do |config|
    servers=[
        {
          :hostname => "control",
          :box => "bento/ubuntu-22.04",
          :ip => "192.168.30.29",
          :ssh_port => '2200'
        },
        {
          :hostname => "jenkins",
          :box => "bento/ubuntu-22.04",
          :ip => "192.168.30.30",
          :ssh_port => '2201'
        },
        {
          :hostname => "maven",
          :box => "bento/ubuntu-22.04",
          :ip => "192.168.30.31",
          :ssh_port => '2202'
        },
        {
          :hostname => "sonarqube",
          :box => "bento/ubuntu-22.04",
          :ip => "192.168.30.32",
          :ssh_port => '2203'
        },
        {
          :hostname => "argoCD",
          :box => "bento/ubuntu-22.04",
          :ip => "192.168.30.33",
          :ssh_port => '2204'
        },
        {
          :hostname => "kubernetes",
          :box => "bento/ubuntu-22.04",
          :ip => "192.168.30.34",
          :ssh_port => '2205'
        }
      ]

    servers.each do |machine|
        config.vm.define machine[:hostname] do |node|
            node.vm.box = machine[:box]
            node.vm.hostname = machine[:hostname]
            node.vm.network :private_network, ip: machine[:ip]
            node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
            node.vm.provider :virtualbox do |vb|
                vb.customize ["modifyvm", :id, "--memory", 512]
                vb.customize ["modifyvm", :id, "--cpus", 1]
            end
        end
    end
end