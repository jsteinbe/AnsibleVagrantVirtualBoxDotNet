# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu14-cloudimage"
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"


  # Update log every time Vagrant is brought up with Date and IP address (Note: Only works with IPv4)

  ip_address_regex  = "([0-9]{1,3}[\.]){3}[0-9]{1,3}"
  ip_address_source = "http://checkip.dyndns.org"
  file_to_write     = "vagrant_up_history_with_ip.txt"

  # Run shell command to write Date/IP to file
  config.vm.provision "shell", privileged: false, run: "always", inline: <<-SHELL
    echo `date` '|' `wget -q "#{ip_address_source}" -O - |  grep -E -o "#{ip_address_regex}"` >> #{file_to_write}
  SHELL


  # Use Ansible to configure the Virtual Machine
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end

end
