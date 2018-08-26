# Require Vagrant version 1.7.0 or above...
Vagrant.require_version ">= 1.7.0"

Vagrant.configure(2) do |config|

  # VagrantClound OS Reference:
  config.vm.box = "ubuntu/trusty64"

  # Network Configuration:
  config.vm.network :forwarded_port, host: 7654, guest: 443, auto_correct: true
  config.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
  config.vm.network "private_network", ip: "10.150.0.3"

  # If true, then all HTTP redirects will be treated as trusted. 
  # That means credentials used for initial URL will be used for all subsequent redirects. 
  # By default, redirect locations are untrusted so credentials (if specified) used only for initial HTTP request.
  # config.vm.box_download_location_trusted = true

  # Disable the new default behavior introduced in Vagrant 1.7, to
  # ensure that all Vagrant machines will use the same SSH key pair.
  # See https://github.com/mitchellh/vagrant/issues/5005
  config.ssh.insert_key = false

  # Set provisioning rules for Ansible:
  config.vm.provision "ansible" do |ansible|
    # ansible.verbose = "vvvv"
    ansible.verbose = "v"
    ansible.playbook = "playbook.yml"
    ansible.become = true
  end
end
