Vagrant.configure("2") do |config|
    config.vm.define "whonix" do |whonix|
      whonix.vm.box = "grml/grml64-full"
      whonix.vm.hostname = "whonix"
      whonix.vm.network "private_network", ip: "192.168.33.10"
      whonix.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
        vb.cpus = 2
      end
    end
  
    config.vm.define "debian" do |debian|
      debian.vm.box = "debian/buster64"
      debian.vm.hostname = "debian"
      debian.vm.network "private_network", ip: "192.168.33.11"
      debian.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
        vb.cpus = 2
      end
    end
  
    config.vm.define "kali" do |kali|
      kali.vm.box = "generic/debian10"
      kali.vm.hostname = "kali"
      kali.vm.network "private_network", ip: "192.168.33.12"
      kali.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
        vb.cpus = 2
      end
      kali.vm.provision "shell", inline: <<-SHELL
        echo "deb http://http.kali.org/kali kali-rolling main contrib non-free" > /etc/apt/sources.list.d/kali.list
        apt-key adv --keyserver hkp://keys.gnupg.net --recv-keys 7D8D0BF6
        apt-get update
        apt-get install -y kali-linux-default
      SHELL
    end
  end
  