Vagrant.configure(2) do |config|
  config.vm.box_check_update = false
  config.vm.box = "centos/7"
  config.vm.hostname = "TestEnv"
  config.ssh.port = 2222
  config.vm.network "forwarded_port", guest: 3306, host: 3306
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "forwarded_port", guest: 50000, host: 50000
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "8192"
  end
end