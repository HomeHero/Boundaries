# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  APP_DIR = '/opt/boundaries.io'.freeze

  config.vm.box = 'ubuntu/trusty64'

  config.vm.hostname = 'geobox'

  config.vm.network 'forwarded_port', guest: 1080, host: 80, auto_correct: true

  config.vm.network 'private_network', ip: '192.168.33.10'

  # config.vm.network 'public_network'

  config.vm.synced_folder '.', APP_DIR, create: true

  config.vm.provider 'virtualbox' do |vb|
    vb.cpus = '2'
    vb.memory = '4096'
  end

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = './provisioner/playbook.yml'
  end

  config.push.define "heroku" do |push|
    push.app = "safe-gorge-76327"
  end

end
