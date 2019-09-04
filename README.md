This will tell you how to create virtual machine on your system to work on diffrent enviroment or OS.

To create VM you have install Oracle VM VirtualBox https://www.virtualbox.org/ and vagrant https://www.vagrantup.com/downloads.html

you can find many vm boxes on https://app.vagrantup.com/boxes/search iam using ubuntu/trusty64

make file 'Vagrantfile' in your directory

copy & paste below code

Vagrant.configure(2) do |config|  
  config.vm.box = "ubuntu/trusty64"  # vm ubuntu 14.04 
  config.vm.network "forwarded_port", guest: 80, host: 8080 # forwarded port 
  config.vm.network "private_network", ip: "192.168.33.10"  # this is your forwarded i.p 

 below command will auto run after vm installed 
 you can add more commands as per your requirement 
 I need nginx with nodeJs auto installed in vm at time of vm installation you can add more as per your requirement

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo add-apt-repository ppa:nginx/stable
    sudo apt-get install -y software-properties-common
    sudo apt-get update
    sudo apt-get install -y nginx

    curl -sL https://deb.nodesource.com/setup | sudo bash -
    sudo apt-get install -y nodejs
  SHELL
end  


<b>Run command from PowerShell on windows for linux/mac from terminal</b>

<strong>Steps to followed</strong>

1. go to directory which you have place Vagrantfile from terminal
2. $ vagrant up  # this will create vm on your system for 1st time it will take few minutes
3. $ vagrant ssh # now you are in vm machine through terminal if it asking password enter 'vagrant'
4. $ lsb_release -a # this will display ubuntu vesion 
5. $ nignx -v , $ node -v  # all these pre installed  


Note: I am using below Version 

Oracle VM VirtualBox Version : 6.0
vagrant : 2.2.3
OS : windows 10 home edition 







