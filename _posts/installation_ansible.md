---
title: 'Installation Ansible Ubuntu, Debian , CentOS'
date: '2024-06-24'
---

<div  align="center">
  <img src="https://i.imgur.com/xir0IXC.png" width="100%"/>
</div>

<div>
<br/>

</div>

# Installation sur CentOS

Ici nous allons apprendre √† installer© Ansible sur diff√rents syst√mes Linux

# Why specifically Alacritty?

Alacritty is fast terminal & highly customizable terminal built on Rust with a strong, growing community. That's all we need! :D

# Alacritty

Let's install and configure Alacritty then üòâ

## Installation

- Arch:
  ```bash
  $ yay -S alacritty
  ```
- Fedora:
  ```bash
  $ sudo dnf install alacritty
  ```

## Installation d'Ansible sur CentOS

- On met √†jour les repos sur notre OS:

  ```bash
  $ sudo yum update

  ```

- On va installer les epel-release 

  ```bash
  $ sudo yum install -y epel-release
  ```

  




```bash
  $ sudo nano ~/.config/alacritty/alacritty.yml
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
  And vouala! Must work just fine üêá
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
