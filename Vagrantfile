Vagrant.configure('2') do |config|
  config.vm.box = 'ubuntu/xenial64'

  config.vm.hostname = 'my-app'

  config.vm.network :private_network, ip: '192.168.0.100'

  config.vm.provider :virtualbox do |vb|
    vb.gui = false
    vb.cpus = 4
    vb.memory = 4096
    vb.customize ['modifyvm', :id, '--natdnsproxy1', 'off']
    vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'off']
  end

  config.disksize.size = '30GB'
  config.mutagen.orchestrate = true

  config.vm.synced_folder 'app', '/home/vagrant/app', type: "rsync",
    rsync_auto: true,
    rsync__exclude: ['.git/', 'node_modules/', 'log/', 'tmp/']

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    ## install brew
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
    echo 'export PATH="/home/linuxbrew/.linuxbrew/bin:$PATH"' >>  ~/.bashrc
    set -i
    source ~/.bashrc

    ## install sam cli
    brew install gmp
    brew install gcc
    brew tap aws/tap
    brew install aws-sam-cli

    ## install aws cli
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    sudo apt install unzip
    unzip awscliv2.zip
    sudo ./aws/install

  SHELL

  config.vm.provision :docker, run: 'always'
  config.vm.provision :docker_compose

end