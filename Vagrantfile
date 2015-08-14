# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

$image = 'ubuntu-14-04-x64'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.hostname = 'ldsc' # comatose, meathead, rocksteady

    config.ssh.private_key_path = '~/.ssh/id_rsa'
    config.vm.box = 'digital_ocean'
    config.vm.box_url = 'https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box'
    config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'" # Stop "stdin: is not a tty" messages

    config.vm.provider :digital_ocean do |provider|
        provider.token = ENV['TOKEN']
        provider.image = $image
        provider.size = '512MB'
        provider.ssh_key_name = ENV['SSH_KEY_NAME']
        provider.setup = false
        provider.private_networking = false
        provider.user_data = File.read('user-data.yml')
        provider.region = 'lon1'
        provider.ipv6 = false
    end
end