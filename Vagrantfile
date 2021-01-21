Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-20.04"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y git zip wget build-essential

    ## Scala setup
    # java
    apt-get install default-jdk
    # Sbt
    echo "deb https://dl.bintray.com/sbt/debian /" | sudo tee -a /etc/apt/sources.list.d/sbt.list
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 642AC823
    apt-get update
    apt-get install sbt

    ## Ocaml setup
    sudo add-apt-repository ppa:avsm/ppa
    sudo apt update
    sudo apt install opam
    opam init --disable-sandboxing
    sudo apt install opam

    opam install -y ocamlfind
    opam install -y ocamlbuild
    opam install -y ounit
  SHELL
end
