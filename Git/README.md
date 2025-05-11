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
``git config --global init.defaultBranch main``		Pour nommer tout les branches initiaux creer à **main**

### Configurez l’éditeur
``git config --global core.editor notepad++``			notepad++
``git config --global core.editor "code --wait"`` 
ou 
``git config --global core.editor "code -w"``	vscode

``git config --global merge.tool vimdiff``

Pour vérifier que vos paramètres ont bien été pris en compte, et vérifier les autres paramètres, il suffit de passer la commande  
``git config --list``

## Initialisez et utilisation de Git votre dépôt local 

### Configuration du SSH

1. Génération d’une nouvelle clé SSH
``ssh-keygen -t ed25519 -C "burkinar@gmail.com" ``

2. Afficher la clé pubique
``cat  /Users/stephane/.ssh/id_ed25519.pub``

3. Créer et iInserer la clé dans les paramettres de GitHub

### Gestion du projet
Initialisons le projet
``git init``

Permet de savoir à tout moment où en est dans notre projet versionné avec git
``git status``

Pour ajouter un fichier à notre projet
``git add <nom_fichier> <nom_fichier>``  ou ``git add .`` 

Pour enregistrer les modifications opérées dans notre projet, doit être précédé d'un git add
``git commit -m "message" ``	ou ``git commit`` pour ouvrr un editeur de texte

Pour choissir la branche 
``git branch -M main``

On verifie si le depot distant existe
``git remote add origin https://github.com/burkinar/MD-Git-Python-Django-Wagtail-uv-pyenv.git``

Pour pousser les modifications en local sur le repository distant de GitHub
``git push -u origin main``

Pour une simplication des commande à faires quand on modifie un fichier
``git add .`` 
``git commit -m "message" 
``git push origin main``	ou ``git push``

Pour récupérer les modifications du repository distant sur notre projet en local.
``git pull``

Commande pour voir les commit realisé au cours de l'edition du projet
``git log``
ou
``git log -1`` => pour afficher la dernière modification enregistrée (dernier commit)

Pour cloner le projet sur notre machine locale
``git clone https://github.com/nom_compte/nom_projet.git``

## Appréhendez le système de branches
### Creation et gestion d'une branche
Voir la list de nos branches
``git branch``
#### option 1
Créer une branche
`` git branch nom_branche``

Commande permet de nous positionner sur la branche crée
``git checkout nom_branche``

#### option 2
Créé la nouvelle branche et nous place dessus pour enregistrer nos modifications
``git checkout -b nom_branche ``

Faire les modification sur les fichiers que nous desirona

1. ``git add .``
2. ``git commit -m "La description du commit" ``
3. ``git push origin test``

### Fusion d'une branche avec la branche principal
Selectionnons la branche main 
``git checkout main``

Verifions si nous sommes sur la branche
``git branch``

Pour fusionner une branche lorsqu'on est placé sur le master (la branche principale du projet)
``git merge nom_branche``

Supprimer une branche
``git branch -d nom_branche

Pour renommer la branche pricipal a **main**
``git branch -M main``

## Travaillez avec un dépôt distant
Accédez à un dépôt distant
``git clone lien_https``

Mettez à jour le dépôt en local
Imaginons que durant la semaine, un de vos amis ait ajouté des modifications sur la branche main et que vous souhaitiez les récupérer.  Comment faire ?

Assurez-vous d’être dans le dépôt :
``git pull origin main``

