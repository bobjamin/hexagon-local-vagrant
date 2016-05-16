$IPINFO = <<-SHELL
  ifconfig eth1 | grep 'inet addr:' | cut -d: -f2 | awk '{ print $1}'
SHELL
$BOX = "ubuntu/trusty64"
$BRIDGE = "en0: Wi-Fi (AirPort)"


Vagrant.configure("2") do |config|
  config.vm.define "host1" do |h|
    h.vm.box = $BOX
    h.vm.network "public_network", bridge: $BRIDGE
    h.vm.provistion "docker"
    h.vm.provision "shell", inline: $IPINFO
    h.vm.synced_folder "../../hexagon", "/vagrant"
  end
  config.vm.define "host2" do |h|
    h.vm.box = $BOX
    h.vm.network "public_network", bridge: $BRIDGE
    h.vm.provision "shell", inline: $IPINFO
    h.vm.synced_folder "../../hexagon", "/vagrant"
    h.vm.synced_folder "../../hexagon/data", "/data"
    h.vm.provision "docker" do |docker|
      docker.run "neo4j",
        args: "--publish=7474:7474 --publish=7687:7687 --volume=/data:/data"
    end
    h.vm.provider "virtualbox" do |vb|
      # Display the VirtualBox GUI when booting the machine
      vb.gui = false
      # Customize the amount of memory on the VM:
      vb.memory = "4096"
    end
  end
end
