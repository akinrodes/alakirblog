---
title: 'Git tips'
date: '2024-06-29'
---

<div  align="center">
  <img src="https://i.imgur.com/xir0IXC.png" width="100%"/>
</div>

<div>
<br/>

</div>

# Git et github

Pour configurer Git afin d'utiliser l'authentification par clé SSH et éviter les demandes de mot de passe, suivez ces étapes :

## 0. Générez les clés ssh en local et les cller sur github

  ```bash
     ssh-keygen
  ``` 

## 1. Vérifier la clé SSH
Assurez-vous que votre clé SSH est ajoutée à votre agent SSH et qu'elle est correctement configurée sur votre compte Git.

Ajouter la clé SSH à l'agent SSH :
  ```bash
  eval $(ssh-agent -s)  # Démarrer l'agent SSH
  ssh-add ~/.ssh/id_rsa  # Ajouter votre clé privée SSH
  ```


## 2. Configurer l'URL du dépôt Git pour utiliser SSH

Assurez-vous que l'URL de votre dépôt distant utilise le format SSH. Voici comment vous pouvez vérifier et modifier cela :

Vérifier l'URL du dépôt :

  ```bash
  git remote -v
  ```

Si l'URL est en HTTPS (par exemple, https://github.com/username/repo.git), vous devez la changer en format SSH (par exemple, git@github.com:username/repo.git).

NB: utiliser remote set-url permet de modifier aisément l'url mais aussi en passant du format https au format ssh 

Modifier l'URL du dépôt : 

  ```bash
  git remote set-url origin git@github.com:username/repo.git
  ```

## 3. Désactiver l'authentification par mot de passe (facultatif)

Si vous voulez vous assurer que Git utilise toujours l'authentification par clé SSH, vous pouvez désactiver la méthode d'authentification par mot de passe dans votre configuration SSH.
Modifier le fichier de configuration SSH :

Ouvrez ou créez le fichier ~/.ssh/config :

  ```bash
  nano ~/.ssh/config
  ```

Ajoutez les lignes suivantes pour configurer l'authentification par clé SSH pour Github:

  ```bash
  Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa
    PreferredAuthentications publickey
  ```

Assurez-vous que le chemin IdentityFile pointe vers votre clé privée SSH.



## 4. Tester la configuration
Pour vérifier que tout fonctionne correctement, utilisez la commande suivante pour tester la connexion SSH avec GitHub :

  ```bash
  ssh -T git@github.com 
  ```



## 5. Pousser vos commits

  
  ```bash
  git push origin main  # Remplacez 'main' par la branche appropriée si nécessaire
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
