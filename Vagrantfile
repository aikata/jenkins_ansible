Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.define "ansible" do |ansible|
    ansible.vm.network "forwarded_port", guest: 22, host: 2220,
      auto_correct: true
  end
  config.vm.define "nginx01" do |nginx01|
    nginx01.vm.network "forwarded_port", guest: 22, host: 2221,
      auto_correct: true
  end
  config.vm.define "nginx02" do |nginx02|
    nginx02.vm.network "forwarded_port", guest: 22, host: 2222,
      auto_correct: true
  end
end
