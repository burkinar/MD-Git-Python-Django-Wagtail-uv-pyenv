# Les commandes utilisées dans le tuto :

## Configurez votre identité
``git config --global user.name "samandoulougou Stephane" ``
``git config --global user.email burkinar@gmail.com``

Grâce à l’option --global, vous n’aurez besoin de le faire qu'une fois.
Si vous souhaitez, pour un projet spécifique, changer votre nom d’utilisateur, vous devrez repasser cette ligne mais sans le **--global**

Pour vérifier que vos paramètres ont bien été pris en compte, et vérifier les autres paramètres, il suffit de passer la commande  
``git config --list``

### Configurez les couleurs
``git config --global color.diff auto``
``git config --global color.status auto``
``git config --global color.branch auto``

### Configurez l’éditeur
``git config --global core.editor notepad++``			notepad++
``git config --global core.editor "code --wait"`` 
ou 
``git config --global core.editor "code -w"``	vscode

``git config --global merge.tool vimdiff``

Pour vérifier que vos paramètres ont bien été pris en compte, et vérifier les autres paramètres, il suffit de passer la commande  
``git config --list``

## Initialisez et utilisation de Git votre dépôt local 
``git init``

Permet de savoir à tout moment où en est dans notre projet versionné avec git
``git status``

Pour ajouter un fichier à notre projet
``git add <nom_fichier> <nom_fichier>``  ou ``git add .`` 

Pour enregistrer les modifications opérées dans notre projet, doit être précédé d'un git add
``git commit -m "message" ``

### Envoyez votre commit sur le dépôt distant avec la commande git push

1. Génération d’une nouvelle clé SSH
``ssh-keygen -t ed25519 -C "burkinar@gmail.com" ``

2. Afficher la clé pubique
``cat  /Users/stephane/.ssh/id_ed25519.pub``

3. Créer et iInserer la clé dans les paramettres de GitHub


git clone https://github.com/nom_compte/nom_projet.git  => permet de cloner le projet sur notre machine locale


git push => pour pousser les modifications en local sur le repository distant (ex : ici GitHub)

git pull => pour récupérer les modifications du repository distant sur notre projet en local.

git log -1 => pour afficher la dernière modification enregistrée (dernier commit)

git checkout -b nom_branche => créé la nouvelle branche et nous place dessus pour enregistrer nos modifications

git merge nom_branche => pour fusionner une branche lorsqu'on est placé sur le master (la branche principale du projet)