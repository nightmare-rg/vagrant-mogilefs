# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "mog1" do |mog1|
    mog1.vm.box = "wheezy"

    mog1.vm.network "private_network", ip: "192.168.33.10"

    # install mogilefs from deb
    mog1.vm.provision :shell, inline: 'aptitude update && aptitude -y upgrade'
    mog1.vm.provision :shell, inline: 'aptitude -y install libsys-syscall-perl libcommon-sense-perl libwww-perl libio-stringy-perl libdbi-perl libnet-netmask-perl libperlbal-perl libio-aio-perl'
    mog1.vm.provision :shell, inline: 'cd /vagrant/wheezy && dpkg -i libdanga-socket-perl_1.61-1_all.deb libmogilefs-client-perl_1.17-1_all.deb libmogilefs-utils-perl_2.28-1_all.deb libmogilefs-server-perl_2.70-1_all.deb'
    mog1.vm.provision :shell, inline: 'mkdir -p /var/mogdata/dev1 && chown -R mogile.mogile /var/mogdata'
    mog1.vm.provision :shell, inline: 'rm /etc/mogilefs/mogstored.conf'
    mog1.vm.provision :shell, inline: '/etc/init.d/mogstored start'
    mog1.vm.provision :shell, inline: 'cp /vagrant/wheezy/mogilefsd.conf /etc/mogilefs/'
    mog1.vm.provision :shell, inline: 'cp /vagrant/wheezy/mogilefs.conf /etc/mogilefs/'
    mog1.vm.provision :shell, inline: 'debconf-set-selections <<< "mysql-server mysql-server/root_password password vagrant"'
    mog1.vm.provision :shell, inline: 'debconf-set-selections <<< "mysql-server mysql-server/root_password_again password vagrant"'
    mog1.vm.provision :shell, inline: 'aptitude -y install mysql-server mysql-client'
    mog1.vm.provision :shell, inline: 'mysql -u root -pvagrant < /vagrant/wheezy/dump.sql'
    mog1.vm.provision :shell, inline: 'mysql -u root -pvagrant -e "flush privileges;"'
    mog1.vm.provision :shell, inline: '/etc/init.d/mogilefsd start'

  end

  config.vm.define "mog2" do |mog2|
    mog2.vm.box = "wheezy"

    mog2.vm.network "private_network", ip: "192.168.33.20"

    # install mogilefs from deb
    mog2.vm.provision :shell, inline: 'aptitude update && aptitude -y upgrade'
    mog2.vm.provision :shell, inline: 'aptitude -y install libsys-syscall-perl libcommon-sense-perl libwww-perl libio-stringy-perl libdbi-perl libnet-netmask-perl libperlbal-perl libio-aio-perl'
    mog2.vm.provision :shell, inline: 'cd /vagrant/wheezy && dpkg -i libdanga-socket-perl_1.61-1_all.deb libmogilefs-client-perl_1.17-1_all.deb libmogilefs-utils-perl_2.28-1_all.deb libmogilefs-server-perl_2.70-1_all.deb'
    mog2.vm.provision :shell, inline: 'rm /etc/mogilefs/mogstored.conf'
    mog2.vm.provision :shell, inline: 'mkdir -p /var/mogdata/dev2 && chown -R mogile.mogile /var/mogdata'
    mog2.vm.provision :shell, inline: '/etc/init.d/mogstored start'

  end

  config.vm.define "mog3" do |mog3|
    mog3.vm.box = "wheezy"

    mog3.vm.network "private_network", ip: "192.168.33.30"

    # install mogilefs from deb
    mog3.vm.provision :shell, inline: 'aptitude update && aptitude -y upgrade'
    mog3.vm.provision :shell, inline: 'aptitude -y install libsys-syscall-perl libcommon-sense-perl libwww-perl libio-stringy-perl libdbi-perl libnet-netmask-perl libperlbal-perl libio-aio-perl'
    mog3.vm.provision :shell, inline: 'cd /vagrant/wheezy && dpkg -i libdanga-socket-perl_1.61-1_all.deb libmogilefs-client-perl_1.17-1_all.deb libmogilefs-utils-perl_2.28-1_all.deb libmogilefs-server-perl_2.70-1_all.deb'
    mog3.vm.provision :shell, inline: 'rm /etc/mogilefs/mogstored.conf'
    mog3.vm.provision :shell, inline: 'mkdir -p /var/mogdata/dev3 && chown -R mogile.mogile /var/mogdata'
    mog3.vm.provision :shell, inline: '/etc/init.d/mogstored start'

  end


end
