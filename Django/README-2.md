# Procedure de creation d'un projet Django avec UV

1. Créer et répertoire pour le projet et ouvrir une terminal dans ce répertoire (éventuellement au sein de votre éditeur de code, vscode ou pycharm)
``mkdir nom_dossier``
``cd nom_dossier``
``uv init nom_dossier``

2. 1. Créez un envoronement virtuel avec la derniere version de python installer sur la machine
``uv venv``
ou
2. 2. Créez votre venv avec n'importe quelle version de python (il s'occupe de l'installer)
``uv venv --python 3.12.6``
ou
``uv venv --python 3.11.9``

3. Activer l'environnement virtuel
``source .venv/bin/activate``

4. Installer Django
``uv add django``		commande pour mettre à jour Django ``uv lock --upgrade``

5. Céer le projet avec la commande je nomme tous mes projets config et le point à la fin est important)
``uv run django-admin startproject config .``


6. Créer le repo de code avec 
``git init``

# Procedure de creation d'une application Django

1. Creation d'une Application
``uv run manage.py startapp nom_app_2``	ou 	``uvm stratapp nom_app``

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
``uv run manage.py migrate``

``uv run manage.py createsuperuser``

4. Nous allons lancons le server de devloppement 
``uv run manage.py runserver``



