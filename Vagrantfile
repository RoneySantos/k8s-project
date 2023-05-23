

#################################################################################################################################
#																
# Script Name: Vagrantfile													
# 
# Description: A code to provision 3 VMs for k8s local labs 				
# Author: Marcus Costa														
# Email Address: marcus.asc@gmail.com												
# Execution Sample: Just "vagrant up" :)									
# 
#################################################################################################################################


# Some variables

$route_ip = "192.168.1.254"                         # Configure to your environment gateway ip address
$brdg_int = "Intel PRO/1000 MT Desktop (82540EM)"        # Configure to your environment NIC adapter

Vagrant.configure("2") do |config|
    config.vm.define "k8s-master" do |k8sm|
        k8sm.vm.box = "bento/ubuntu-22.04" # Default generic/debian10
        k8sm.vm.hostname = "k8s-master"
        k8sm.vm.network "public_network", bridge: "#{$brdg_int}" 
        k8sm.vm.provider "virtualbox" do |v| 
            v.memory    = 3048
            v.name      = "k8s-master"
        k8sm.vm.provision "shell",
            run: "always",
            inline: "apt-get install net-tools"
        k8sm.vm.provision "shell",
            run: "always",
            inline: "route del default"    
        k8sm.vm.provision "shell",
            run: "always",
            inline: "route add default gw #{$route_ip}"
        end
    # config.vm.provision "shell", inline: <<-SHELL
    #     apt update -y && apt install vim wget tcpdump curl htop telnet nmap net-tools sysstat -y && curl -fsSL https://get.docker.com | bash && curl -L https://raw.githubusercontent.com/docker/compose/1.29.2/contrib/completion/bash/docker-compose -o /etc/bash_completion.d/docker-compose
    #     SHELL
    # config.vm.provision "file", source: "./.vimrc", destination: "~/.vimrc"
    # config.vm.provision "file", source: "./k8s.conf", destination: "~/k8s.conf"
    # config.vm.provision "file", source: "./daemon.json", destination: "~/daemon.json"
    # config.vm.provision "file", source: "./k8s.sh", destination: "~/k8s.sh"
    # config.vm.provision "shell", inline: <<-SHELL
    #     chmod +x k8s.sh && sed -i 's/\r$//' /home/vagrant/k8s.sh && /home/vagrant/k8s.sh
    # SHELL
    end 
end

# Vagrant.configure("2") do |config|
# Using the number of VM "i" to compose it hostname
#         (1..2).each do |i| 
#             config.vm.define "k8s_#{i}" do |k8s|
#                 k8s.vm.box = "generic/debian10"
#                 k8s.vm.hostname = "k8s-#{i}"
#                 k8s.vm.network "public_network", bridge: "#{$brdg_int}" 
#                 k8s.vm.provider "virtualbox" do |v| 
#                     # Setting up custom settings
#                     v.memory    = 1500
#                     v.name      = "k8s-#{i}"
#                 k8s.vm.provision "shell",
#                     run: "always", 
#                     inline: "route del default"
#                 k8s.vm.provision "shell",
#                     run: "always",
#                     inline: "route add default gw #{$route_ip}"
#                 end
#             config.vm.provision "shell", inline: <<-SHELL
#                 apt update -y && apt install vim wget tcpdump curl htop telnet nmap net-tools sysstat -y && curl -fsSL https://get.docker.com | bash && curl -L https://raw.githubusercontent.com/docker/compose/1.29.2/contrib/completion/bash/docker-compose -o /etc/bash_completion.d/docker-compose
#                 SHELL
#             config.vm.provision "file", source: "./.vimrc", destination: "~/.vimrc"
#             config.vm.provision "file", source: "./k8s.conf", destination: "~/k8s.conf"
#             config.vm.provision "file", source: "./daemon.json", destination: "~/daemon.json"
#             config.vm.provision "file", source: "./k8s.sh", destination: "~/k8s.sh"
#             config.vm.provision "shell", inline: <<-SHELL
#                 chmod +x k8s.sh && sed -i 's/\r$//' /home/vagrant/k8s.sh && /home/vagrant/k8s.sh
#             SHELL
#             end
#         end 
# end
