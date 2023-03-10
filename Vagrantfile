Vagrant.configure("2") do |config|
  config.vm.box = "debian/jessie64" # Используем Debian 8
  config.vm.hostname = "vagrant-task"
  config.vm.disk :disk, size: "10GB", primary: true
  config.vm.network "forwarded_port", guest: 80, host: 80 # Проброс порта для Nginx
  config.vm.network "forwarded_port", guest: 8888, host: 8888 # Проброс порта для Apache
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048" # Установка оперативной памяти 2 GB
    vb.cpus = 2 # Установка двух CPU
  end

  # Применение Ansible playbook для установки необходимых пакетов
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.compatibility_mode = "2.0"
  end
  # Обновить php до 7.2
#     config.vm.provision "ansible" do |ansible|
#       ansible.playbook = "install_php7.2.yml"
#       ansible.compatibility_mode = "2.0"
#     end
end