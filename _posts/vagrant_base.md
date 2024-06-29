---
title: 'Vagrant les bases'
date: '2024-06-29'
---

<div  align="center">
  <img src="https://i.imgur.com/xir0IXC.png" width="100%"/>
</div>

<div>
<br/>

# Vagrant  
On commence par ajouter une box avec laquelle on pourra travailler 

vagrant box add ubuntu/trusty64 

vagrant box add USER/BOX  

Plus de box ici :   https://app.vagrantup.com/boxes/search

## Premier projet, creation d'une machine virtuelle
La première fois que vous exécutez la commande "vagrant up", Vagrant importera (clonera) la boîte vagrant dans VirtualBox et la démarrera.  Si Vagrant détecte que la machine virtuelle existe déjà dans VirtualBox, il la démarrera simplement.  Par défaut, lorsque la machine virtuelle est démarrée, elle est démarrée en mode sans tête, ce qui signifie qu'aucune interface utilisateur pour la machine n'est visible sur votre machine hôte locale.

- Lançons votre première machine virtuelle exécutant Linux avec Vagrant.

  ```bash
  mkdir project_1
  cd project_1
  vagrant init ubuntu/trusty64
  vagrant up
  ```

- Vagrant file

  ```bash
      Vagrant.configure(2) do |config|
      config.vm.box = "ubuntu/trusty64"
      config.vm.hostname = "box1"
      config.vm.network "private_network", ip: "192.168.56.20"
     end
  ```

## Deuxieme projet , creation de deux machines virtuelles

- initialisons et lançons nos machines virtuelles

  ```bash
  mkdir project_2
  cd project_2
  vagrant init ubuntu/trusty64
  ##ici config vagrantfile
  vagrant up
  ```

- Vagrant file

  ```bash
      Vagrant.configure("2") do |config|
        config.vm.box = "jasonc/centos7"
        config.vm.define "test1" do |test1|
          test1.vm.hostname = "test1"
          test1.vm.network "private_network", ip: "10.9.8.5"
        end
        config.vm.define "test2" do |test2|
          test2.vm.hostname = "test2"
          test2.vm.network "private_network", ip: "10.9.8.6"
        end
      end
  ```

## Tests

- Start the virtual machines.  (Remember, that if you do not specify a VM name all the defined VMs will be started.)

  vagrant up 

- Check their status with the following command:

  vagrant status 

- Connect to the test1 virtual machine to confirm that it’s working and then exit it.

  vagrant ssh test1
  $ exit

- Connect to the test2 virtual machine to confirm that it’s working. While you are logged into the test2 VM, ping the test1 VM to prove that the two virtual machines can communicate with each other over the network.

    vagrant ssh test2
    ping -c 3 10.9.8.5

When you brought up the virtual machines you may have noticed a message similar to this one:

==> test2: Mounting shared folders...

   test2: /vagrant => /Users/jason/shellclass/multitest

- You can access the files in the vagrant project directory that resides on your local machine inside the virtual machine.  The vagrant project directory is mounted, or shared, via the /vagrant directory.  The only file in our local directory is the Vagrantfile.  You can look at the file from within the vm.  Run the following commands while you're still logged into the test2 VM:

    ls /vagrant
    cat /vagrant/Vagrantfile

- Exit out of the test2 VM.

    exit 
    Stop the Virtual Machines

- In upcoming projects you'll be working more with Vagrant, virtual machines, IP addresses and more.  
Feel free to explore the Linux system if you'd like.  
(Connect by running "vagrant ssh [VM_NAME]" within the project folder.) 
 When you're ready to stop or take a break, halt the virtual machine.  Remember, you can always pick up where you left off as long as you don't destroy the virtual machine.

    vagrant halt 

Les machines virtuelles sont toujours présentes . On peut les voir dans l'état poweroff sur le provider VirtualBox
Faut penser à les détruire si tu veux plus les utiliser.

    vagrant destroy
