# -*- mode: ruby -*-
# vi: set ft=ruby :

Dotenv.load

# change default provider to digital_ocean
ENV['VAGRANT_DEFAULT_PROVIDER'] = "digital_ocean"

# set droplet image name
# if you want to know available image names, please type below.
#   vagrant digitalocean-list images <TOKEN>
IMAGE_NAME = 'centos-7-2-x64'

Vagrant.configure(2) do |config|
  config.vm.hostname = 'dev.daicham.com'
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider :digital_ocean do |provider, override|
    override.ssh.private_key_path = '~/.ssh/id_rsa'
    override.vm.box = 'digital_ocean'
    override.vm.box_url = "https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box"

    provider.token = ENV['PERSONAL_TOKEN']
    provider.image = IMAGE_NAME
    provider.region = 'sgp1'
    provider.size = '2gb'
    provider.ssh_key_name = ENV['SSH_KEY_NAME'] || 'Vagrant'
  end
end
