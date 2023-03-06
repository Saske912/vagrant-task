Vagrant.configure("2") do |config|
  config.vm.box = "debian/jessie64" # Используем Debian 8
  config.vm.hostname = "myvm"
  config.vm.network "forwarded_port", guest: 80, host: 2080 # Проброс порта для Nginx
  config.vm.network "forwarded_port", guest: 8888, host: 2088 # Проброс порта для Apache
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048" # Установка оперативной памяти 2 GB
    vb.cpus = 2 # Установка двух CPU
  end

  # Установка Ansible внутри виртуальной машины
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y software-properties-common
    apt-add-repository ppa:ansible/ansible
    apt-get update
    apt-get install -y ansible
  SHELL

  # Применение Ansible playbook для установки необходимых пакетов
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end