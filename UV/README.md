# Installation standalone de uv, un remplaçant de pip, pip-tools, pipx, pipenv/poetry, pyenv, virtualenv 10 à 100x plus rapide que pip : 

Reference d'installation:
https://earthly.dev/blog/python-uv/
https://www.datacamp.com/fr/tutorial/python-uv

##  MacOS & linux : 
``$ curl -LsSf https://astral.sh/uv/install.sh | sh``

On Mac, you also have the option to install uv via Homebrew:

``$ brew install uv``

## Windows: 
``$ powershell -c "irm https://astral.sh/uv/install.ps1 | iex"``

C'est tout ! Redémarrez est c'est utilisable !

Vous pouvez ensuite vérifier l'installation en lançant `uv version`:

``uv version``

# Création  d'envoronement virtuel 

**Créez un envoronement virtuel avec la derniere version de python installer sur la machine**
``$ uv venv``

**Créez votre venv avec n'importe quelle version de python** (il s'occupe de l'installer)
``uv venv --python 3.12.6``
ou
``uv venv --python 3.11.9``

**Créez un venv avec un nom specifique et comme exemple ici on cre un envirronnrment virtuel nommé "test" avec n'importe quelle version de python** (il s'occupe de l'installer)
``$ uv venv test --python 3.11.9``

**Pour activer l'environnement virtuel**
``$ source .venv/bin/activate``
ou
**Pour activer l'environnement virtuel avec un nom specifiques**
``$ source test/bin/activate``

**Pour desactiver l'environnement virtuel**
``$ deactivate``

**Pour supprimer un environnement virtuel activé**
``$ rm -rf my_second_env``

Vous avez le contrôle absolu de la version de python que vous utilisez dans votre venv.

# Installation de paquet avec UV

## Installer plusieurs version de python sur machine

Pour installer la dernière version de Python :

``uv python install``

**Installation de n'importe quelle version de python sans crer un environnement virtuel**
``uv python install 3.12``

To install multiple Python versions:
``uv python install 3.9 3.10 3.11``

Pour installer une version qui satisfait les contraintes :
``uv python install '>=3.8,<3.10'``

**Afficher toutes les version python installer sur la machine. **
Reference:
Pour consulter toutes les versions de Python https://www.python.org/doc/versions/
``uv python list``

To filter the Python versions, provide a request, e.g., to show all Python 3.13 interpreters:
``uv python list 3.13``

Or, to show all PyPy interpreters:
``uv python list pypy``

By default, downloads for other platforms and old patch versions are hidden.
To view all versions:
``uv python list --all-versions``

To view Python versions for other platforms:
``uv python list --all-platforms``

To exclude downloads and only show installed Python versions:
``uv python list --only-installed``

Supprimer une version python installée par le gestionnaire de paquet UV
 ``uv python uninstall 3.12.6``
 
# Gestionnaire de paquet et d'outil python avec UV

Reference https://docs.astral.sh/uv/pip/packages/

## Installation de paquet python

Installation d'un package
Pour installer un package dans l'environnement virtuel, par exemple djiango :
Reference: https://pypi.org/project/Django/#history

Installer un paquet dans son envirronnrment virtuel de développement
``uv pip install django``

Installer un paquet avec une version specifique dans son envirronnrment virtuel de développement
``uv pip install 'django==5.2'``

To install multiple packages, e.g., Django and Ruff:
``uv pip install django ruff``

## Installation des outils python

Commande pour installer des outils
``uv tool install`` ou ``uvx``

**Tester des outils python** sans installation (ici usage de la dernière version de cookiecutter sans installation) :

``uvx cookiecutter gh:start-new/postgres``

**Installer un outil python de manière isolée**

``uv tool install cookiecutter``

Installer les outil par version
``uvx ruff@0.6.0 --version``

Installer la derneire version
``uvx ruff --version``
``uvx ruff@latest --version``

``uv tool install ruff==0.5.0``

``uv tool install ruff@latest``
``uv tool install ruff@0.6.0``

Upgrading tools
``uv tool upgrade black``

Uninstall a tool
``uv tool uninstall black``


# Gestionnaire de paquet python avec UV

Reference: https://www.datacamp.com/fr/tutorial/python-uv

## Gérez les environnements virtuels à l'aide du fichier requirements.txt

Le fichier requirements.txt  contient la liste des paquets Python dont l'installation est requise dans un environnement virtuel pour que l'application s'exécute correctement

Nous pouvons afficher les paquets que nous avons installés dans notre environnement virtuel à l'aide de la commande pendant que l'environnement est actif.
``uv pip freeze``

Créer un fichier  **requirements.txt **  automatiquement et mettre tous les paquets installer
``uv pip freeze > requirements.txt``

# UV pour la gestion des dépendances du projet

Je viens de l'école des outils pip , qui propose une solution très simple pour résoudre ce problème. Il suffit de conserver les exigences de base dans un **requirements.in** fichier ressemblant à ceci : ``django>=5.0``

Ensuite, vous exécutez une commande comme celle-ci pour générer votre **requirements.txt** fichier :
``uv pip compile requirements.in -o requirements.txt``
ou pour plusieurs fichier on utilise cette commande
``uv pip compile pyproject.toml requirements-dev.in -o requirements-dev.txt``



**Créer le pyproject.toml** de son projet:

$ uv init



**Installation de Django** dans son projet

$ uv add django