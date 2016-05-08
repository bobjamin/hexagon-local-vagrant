Vagrant.configure("2") do |config|
  config.vm.define "host1" do |h1|
    h1.vm.box = "hashicorp/precise64"
    h1.vm.network "public_network", bridge: "en0: Wi-Fi (AirPort)"
    h1.vm.provision "docker" do |d|

    end
  end
  config.vm.define "host2" do |h2|
    h2.vm.box = "hashicorp/precise64"
    h2.vm.network "public_network", bridge: "en0: Wi-Fi (AirPort)"
    h2.vm.provision "docker" do |d|

    end
  end
end
