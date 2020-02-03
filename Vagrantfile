# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.provision "shell", inline: <<-SHELL
    export LC_ALL="en_US.UTF-8"
    apt-get update
    apt-get install -y build-essential g++ gcc make autoconf automake bison flex \
      libncurses5-dev libreadline-dev libusb-dev texinfo subversion doxygen libgmp3-dev \
      graphviz libtool unrar unzip cmake wget pkg-config unzip bsdtar alien dpkg wget zlib1g-dev
    wget https://master.dl.sourceforge.net/project/minpspw/SDK%20%2B%20devpak/pspsdk%200.11.1/minpspw_0.11.1-1ubuntu0_amd64.deb
    dpkg -i minpspw_0.11.1-1ubuntu0_amd64.deb
    sudo ln -s /usr/lib/x86_64-linux-gnu/libgmp.so.10 /usr/lib/libgmp.so.3
    echo "export PATH=$PATH:/opt/pspsdk/bin" >> /home/vagrant/.profile
    echo "export PSPSDK=/opt/pspsdk" >> /home/vagrant/.profile
    wget -c https://codeload.github.com/dogo/oslibmodv2/zip/master
    unzip master
    cd oslibmodv2-master
    cp -R src/* /opt/pspsdk/psp/include/oslib
    cp -R libosl.a /opt/pspsdk/psp/lib
  SHELL
end