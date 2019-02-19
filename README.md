# amhello

+ This is sample files for `autoconf` and `automake`.

+ The log is here: https://gist.github.com/knknkn1162/6488607a43e7cb754478f270dd7131a7.

```bash
# If there is `configure.ac` in the project, you can setup the package initially.
autoreconf --install
configure
make
make install
# You can distribute the package by the below command. At last, amhello-1.0.tar.gz is generated.
make distcheck
```

# environments

```Vagrantfile
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
  config.vm.box = 'ubuntu/bionic64'
  config.vm.synced_folder './', '/home/vagrant/shared'
  config.vm.provider 'virtualbox' do |vb|
    vb.memory = '2048'
    vb.cpus = 2
  end
  config.vm.provision 'shell', inline: <<-SHELL
    apt-get update
    apt-get install -y gcc make autotools-dev automake pkg-config
  SHELL
end
```
