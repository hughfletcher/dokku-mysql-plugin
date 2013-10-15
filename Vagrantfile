$provision = <<SCRIPT
wget -qO- https://raw.github.com/progrium/dokku/master/bootstrap.sh | bash
apt-get install -y shunit2
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.define :dokku do |dokku|
    dokku.vm.box = "raring64"
    dokku.vm.box_url = "http://cloud-images.ubuntu.com/raring/current/raring-server-cloudimg-vagrant-amd64-disk1.box"
    dokku.vm.network :private_network, ip: "192.168.33.10"
    dokku.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
      vb.customize ["modifyvm", :id, "--name", "dokku-mysql-plugin"]
    end
    dokku.vm.synced_folder ".", "/var/lib/dokku/plugins/mysql", owner: "root", group: "root"
    dokku.vm.provision :shell, :inline => $provision
  end
end