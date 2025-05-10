# Description de Pyenv

Pyenv permet d'installer plusieur version de python sur sa machine de developpement 

## Étape 1 : Intallation de pyenv
Lien: https://github.com/pyenv/pyenv?tab=readme-ov-file

## Étape 2 :Utlisation de Pyenv

1. Voir la liste des python installer sur la machine
``pyenv install -l``
La version installable sur la machine est cpython qui contient uniquement les numeros des versions.

2. Install additional Python versions
``pyenv install 3.10.4``

Sur le mac nous avons installer 3 versions de python
3.112
3.12.4
3.13.0

3. Basculer entre les versions de Python

Pour sélectionner une version de Python installée avec Pyenv comme version à utiliser, exécutez l'une des commandes suivantes :

``pyenv shell <version>`` -- sélection uniquement pour la session shell en cours
``pyenv local <version>`` -- sélection automatique lorsque vous êtes dans le répertoire courant (ou ses sous-répertoires)
``pyenv global <version>`` -- sélection globale pour votre compte utilisateur

Utiliser **« system »** comme nom de version réinitialiserait la sélection à la version Python fournie par votre système.

Rendre plusieurs versions disponibles
Vous pouvez sélectionner plusieurs versions de Python simultanément en spécifiant plusieurs arguments. Par exemple, si vous souhaitez utiliser les dernières versions de Python 3.11 et 3.12 installées :
``pyenv global 3.11 3.12``

Chaque fois que vous exécutez une commande fournie par une installation Python, ces versions sont recherchées dans l'ordre spécifié. En raison du comportement de basculement des shims, la recherche implicite est toujours effectuée sur la version système.

## Étape 3: Créer un environnement virtuel

``python3 -m venv venv``

## Étape 4 : Activer l’environnement virtuel

``source venv/bin/activate``

