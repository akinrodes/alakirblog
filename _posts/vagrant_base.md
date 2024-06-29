---
title: 'On d�marre notre voyage avec Ansible'
date: '2024-06-24'
---

<div  align="center">
  <img src="https://i.imgur.com/xir0IXC.png" width="100%"/>
</div>

<div>
<br/>

</div>

# Installlation, premiers playbooks

Ici nous allons apprendre à installer Ansible sur divers OS Linux, à ecrire des playbooks , à mettre en place des projets de depliement et tests.


## Installation d'Ansible sur Ubuntu, Debian 
  
  ```bash
  sudo apt install -y gnupg2
  echo 'deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main' | sudo tee -a /etc/apt/sources.list
  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
  sudo apt update
  sudo apt install -y ansible
  ```


## Installation d'Ansible sur CentOS

- On met àjour les repos sur notre OS:

  ```bash
  $ sudo yum update

  ```

- On va installer les epel-release 

  ```bash
  $ sudo yum install -y epel-release
  ```

## Decouvrir les commandes AD-HOC

  ```bash
  cat hosts
  10.0.0.4 ansible_user=admin ansible_password=admin ansible_ssh_common_args='-o StrictHostKeyChecking=no'
  10.0.0.5 ansible_user=admin ansible_password=admin ansible_ssh_common_args='-o StrictHostKeyChecking=no'


  ping command
  ansible -i hosts all -m ping


  create file command
  ansible -i hosts all -m copy -a "dest=/home/admin/toto.txt content='bonjour eazytraining'"


  setup command
  ansible -i hosts all -m setup  

  ```

##Decouvrir l'inventaire au format Yaml(Bonnne pratique de securite , toujours mettre une extension aux fichiers:

  cat hosts
  ```bash
  all:
    hosts:
      10.0.0.4:
        ansible_user: admin
        ansible_password: admin
        ansible_ssh_common_args: '-o StrictHostKeyChecking=no'
      10.0.0.5:
        ansible_user: admin
        ansible_password: admin
        ansible_ssh_common_args: '-o StrictHostKeyChecking=no'

  ```
  
  Tests:
  ```bash
  ping command
  ansible -i hosts all -m ping


  create file command
  ansible -i hosts all -m copy -a "dest=/home/admin/toto.txt content='bonjour eazytraining'"

  ```


- Then, add the following (adjust the font and size if needed):

  ```yml
  font:
    normal:
      family: JetBrains Mono
      style: Regular

    bold:
      family: JetBrains Mono
      style: Bold

    italic:
      family: JetBrains Mono
      style: Italic

    bold_italic:
      family: JetBrains Mono
      style: Bold Italic

    size: 12
  ```
<!-- NEOFETCH -->

# Neofetch

Here we will configure Neofetch. If you don't know what it is, let me explain in short: _Neofetch is a command-line tool that shows a visually appealing summary of your system's key information, like OS, kernel, CPU, GPU, and memory, with a colorful ASCII_.

<div  align="center">
  <img width="50%" src="https://i.imgur.com/lY0zB6O.png"/>
</div>


- Finally, we can test it! Simply run the neofetch command pointing to our newly created ASCII file like so:
  ```bash
  $ neofetch  --ascii ~/Pictures/neofetch/art
  ```
  And vouala! Must work just fine 🐇
  <div  align="center">
    <img width="50%" src="https://i.imgur.com/oMFlxVE.png"/>
  </div>

## Adding Neofetch output on Terminal launch

Let's open the config once again and make it run Neofetch with custom ASCII Art location on each start of Alacritty.

```bash
$ sudo nano ~/.config/alacritty/alacritty.yml
```

```yml
shell:
  program: /bin/bash
  args:
    - -c
    - 'neofetch  --ascii ~/Pictures/neofetch/art; exec bash'
```
