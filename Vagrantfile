# http://TeroKarvinen.com/
# vim: filetype=ruby

$tscript = <<TSCRIPT
apt update
apt install -y puppet
echo "172.28.171.19 blue.local" |sudo tee --append /etc/hosts
echo "[agent]"|sudo tee --append /etc/puppet/puppet.conf
echo "server = blue.local"|sudo tee --append /etc/puppet/puppet.conf
puppet agent --enable
service puppet restart
TSCRIPT


Vagrant.configure(2) do |config|
 config.vm.box = "bento/ubuntu-16.04"
 config.vm.provision "shell", inline: $tscript

 config.vm.define "slave01" do |slave01|
   slave01.vm.hostname = "slave01"
 end

 config.vm.define "slave02" do |slave02|
   slave02.vm.hostname = "slave02"
 end
end
