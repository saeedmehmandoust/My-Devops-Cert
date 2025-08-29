Vagrant.configure("2") do |config|
  config.vm.box = "bento/debian-12"   # Debian 12

  config.vm.provider "vmware_desktop" do |v|
    v.gui = true
    v.memory = 2048
    v.cpus = 2
  end
end