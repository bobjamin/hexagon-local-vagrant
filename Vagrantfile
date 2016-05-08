$IPINFO = <<-SHELL
  ifconfig eth1 | grep 'inet addr:' | cut -d: -f2 | awk '{ print $1}'
SHELL
$BOX = "ubuntu/trusty64"
$BRIDGE = "en0: Wi-Fi (AirPort)"


Vagrant.configure("2") do |config|
  config.vm.define "host1" do |h|
    h.vm.box = $BOX
    h.vm.network "public_network", bridge: $BRIDGE
    h.vm.provision "docker"
    h.vm.provision "shell", inline: $IPINFO
  end
  config.vm.define "host2" do |h|
    h.vm.box = $BOX
    h.vm.network "public_network", bridge: $BRIDGE
    h.vm.provision "docker"
    h.vm.provision "shell", inline: $IPINFO
  end
end
