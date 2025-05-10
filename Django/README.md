# Procedure de creation d'un projet Django

1. Créer et répertoire pour le projet et ouvrir une terminal dans ce répertoire (éventuellement au sein de votre éditeur de code, vscode ou pycharm)
``mkdir nom_dossier``
``cd nom_dossier``

2. 1. Créez un envoronement virtuel avec la derniere version de python installer sur la machine
``$ uv venv``
ou
2. 2. Créez votre venv avec n'importe quelle version de python (il s'occupe de l'installer)
``$ uv venv --python 3.12.6``
ou
``$ uv venv --python 3.11.9``

3. Activer l'environnement virtuel
``$ source .venv/bin/activate``

4. Céer le projet avec la commande je nomme tous mes projets config et le point à la fin est important)
``django-admin startproject config .``

5. Créer le repo de code avec 
``git init``

# Procedure de creation d'une application Django

1. Creation d'une Application
``python manage.py startapp nom_app``

2. ouvrir le ficher setting.py de django et declarer l'application crée 
``INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    "nom_app",
]``

3. verifier que cela marche bien, nous allons tous d'abord faire la migration de la base des données
``python manage.py migrate``

4. Nous allons lancons le server de devloppement 
``python manage.py runserver``

# Procedure de creation d'un projet Django avec UV
**Reference:** https://www.datacamp.com/fr/tutorial/python-uv

Cette procedure vise à creer un projet contenent les fichiers initiaux pour un projet python avec le gestionnaire de paquet UV

Initialiser un nouveau projet dans un dossier projet 
``uv init explore-uv``

Si le dossier qui doit contenir le projet est deja crée on utilise ce code pour inititier un projet de base contennant quelques fichier de base qu'on peut utiliser
``uv init .``

Gestion des versions de Python dans UV
Ensuite on verifie quel version de python on veux utiliser pour notre projet en listant d'abord les version python installler sur notre machine de developement
Liste des versions existantes de Python:
`uv python list --only-installed``
``uv python list``

Si la version python que nous voulons utiliser dans notre projet n'est pas present  nous installons avce la commande suivante: par exemple la version 3.12.7
``uv python install 3.12.7``

Un fois que la version de python installer est presente sur la machine de developpement nous creons un environrnrmt de de developpement **venv** mais avant cela  nous modifions les fichers **.python-version**  **pyproject.toml** pour correspondre a la version de notre projet qui est ici la version **3.12.7** et nous supprimon le ficher **uv.lock** s'il existe dans le dossier
``uv venv --python 3.12.7``

On active l'environnement virtuel par:
``source .venv/bin/activate``

Pour installer un paquet python comme django nous utilisons la commande suivante:
``uv add django``
Mise à jour des dépendances
1. Installer la dernière version d'un paquet :
``uv add django``
2. Installation d'une version spécifique :
``uv add django=2.1.2``
3. Modifier les limites des contraintes d'un paquet :
``uv add 'django<3.0.0'``

Pour supprimer une dépendance de l'environnement et du fichier pyproject.toml, vous pouvez utiliser la commande uv remove. Il désinstallera le paquet et toutes ses dépendances :
``uv remove django ``

Exécuter des scripts Python avec UV
``uv run hello.py``

Modifier les versions de Python pour le projet en cours 
Vous pouvez changer de version de Python pour votre projet UV actuel à tout moment, tant que la nouvelle version satisfait aux spécifications de votre fichier pyproject.toml. Par exemple, le fichier suivant nécessite les versions 3.9 et supérieures de Python :	** requires-python = ">=3.9 "**

Cela signifie que vous pouvez changer la version de Python dans le fichier .python-version pour n'importe quelle version supérieure, comme 3.11.7. Appelez ensuite :
``uv sync ``

La commande vérifie d'abord les installations Python existantes. Si la version demandée n'est pas trouvée, UV la télécharge et l'installe dans le chemin d'accès /Users/username/.local/share/uv/python. UV crée également un nouvel environnement virtuel dans le répertoire du projet, qui remplace l'ancien. 

Ce nouvel environnement n'a pas les dépendances listées dans votre fichier pyproject.toml, vous devez donc les installer avec la commande suivante :
``uv pip install -e .``

Notez que les commandes uv peuvent parfois provoquer des erreurs Permission Denied. Dans ce cas, assurez-vous d'utiliser la commande sudo si vous êtes sous macOS ou Linux ou exécutez votre invite de commande avec des privilèges d'administrateur si vous êtes sous Windows. Une meilleure solution consisterait à changer la propriété du répertoire personnel de l'UV en faveur de l'utilisateur :
``sudo chown -R $USER ~/.local/share/uv  # macOS or Linux``

Les fichiers de verrouillage sont essentiels pour le développement afin de maintenir des constructions reproductibles et d'éviter les conflits de dépendance. Les fichiers Requirements.txt sont mieux adaptés aux scénarios de déploiement ou au partage du code avec des utilisateurs qui n'utiliseront peut-être pas UV. Ils sont également nécessaires pour assurer la compatibilité avec les outils et les services qui ne prennent pas en charge le format de fichier de verrouillage de l'UV.

Vous pouvez gérer les deux fichiers en utilisant le fichier de verrouillage de l'UV pour le développement et en générant un fichier requirements.txt pour le déploiement. Pour générer un site requirements.txt à partir d'un fichier de verrouillage UV, utilisez la commande suivante :

``uv export -o requirements.txt``
``uv pip compile pyproject.toml -o requirements.txt``

Vous pouvez gérer les deux fichiers en utilisant le fichier de verrouillage de l'UV pour le développement et en générant un fichier **requirements.txt** pour le déploiement. Pour générer un site **requirements.txt** à partir d'un fichier de verrouillage UV, utilisez la commande suivante :
``uv export -o requirements.txt``

# Passer de PIP et Virtualenv à UV
La migration de PIP et virtualenv vers UV est simple car UV maintient la compatibilité avec les normes d'empaquetage Python existantes. Voici un guide étape par étape pour faciliter la transition :

1. Convertir un projet virtualenv existant
Si vous avez un projet existant utilisant virtualenv et pip, commencez par générer un fichier requirements.txt à partir de votre environnement actuel si ce n'est pas déjà fait :
``uv pip freeze > requirements.txt``

Créez ensuite un nouveau projet UV dans le même répertoire :
``uv init .``

Enfin, installez les dépendances de votre fichier d'exigences :
``uv pip install -r requirements.txt``

Pour obtenir la liste de vos dépendances :
``uv pip freeze``
ou
``uv pip list``


Pour savoir si vous avez des dépendances qui ne sont pas à jour :
``uv pip list --outdated``

Et pour les mettre à jour du coup :
``uv pip install django --upgrade``

autre commande inportante
https://docs.astral.sh/uv/getting-started/features/#projects



