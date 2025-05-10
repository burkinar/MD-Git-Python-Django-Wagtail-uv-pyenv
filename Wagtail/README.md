# Intallation et mise à jour de wagtail CMS avec deux options possible avec UV

# Intallation

1. Intaller un environment virtue
   ``uv venv``
 Activé l'enviroment virtuel
 ``source .venv/bin/activate``
 
 ### option 1 avec uv
1. Ajouter les fichiers initiaux de UV avec les fichiers de veroullages
 ``uv init .``

2. Installer la derniere version ou une autre version de wagtail dans le meme repertoire:
 ``uvx wagtail@latest start <site-name> .`` 
 ou 
 ``uvx wagtail@6.2 start <site-name> .``
 
3. Puis on ajoutes les dependances a installer dans le fichier **pyproject.toml** tous en verifiant les versions que nous desirins installer dans le projet
 ```
 dependencies = [
"Django>=5.1,<5.2",
"wagtail>=6.4,<6.5",]
```
 4. Et on installer les paquet declarer dans par la commande suivante:
 ``uv sync``
 5. On tapes les commandes commande suivantes
 	1. Crée ou mettre à jour une database
``uv run manage.py migrate``		
ou 		
``uvm makemigrations`` ``uvm migrate``
  2. Create an admin user
``uv run manage.py createsuperuser``		ou 		``uvm createsuperuser``
  3. Start the server
``uv run manage.py runserver``		ou 		``uvm runserver``

6. On supprimes les fichier qui ne sont pas necessaires dans le projet 

7. Mettre jour waigtail
8. ``uv tool upgrade wagtail``

### option 2 avec uv et pip

1. INSTALLATION => Installer la derniere version de wagtail ou choisir une version voulu
 ``uv pip install wagtail`` 	
 ou 	
 ``uv pip install wagtail==6.2``
 
 2. Générez votre site wagtail dans le meme repertoire:
 ``uv run wagtail start <site-name> .``
 
 3. Install project dependencies
 ``uv pip install -r requirements.txt``
 
 4. On tapes les commandes commande suivantes
 	1. Crée ou mettre à jour une database
``uv run manage.py migrate``		
ou 	
``uvm makemigrations``	``uvm migrate``
  2. Create an admin user
``uv run manage.py createsuperuser``		ou 		``uvm createsuperuser``
  3. Start the server
``uv run manage.py runserver``		ou 		``uvm runserver``
ou ``uvm runserver 127.0.0.1:8001``

5. On supprimes les fichier qui ne sont pas necessaires dans le projet 
 
 ## Mise à jour
Update the wagtail line in your project’s **requirements.txt** file (or the equivalent, such as **pyproject.toml**) to specify the latest patch release of the version you wish to install. For example, to upgrade to version 6.3.x, the line should read:
``wagtail>=6.3,<7``

Ensuite on excecutes ces commandes
 ``uv pip install -r requirements.txt``
 ``uvm makemigrations``
 ``uvm migrate``
 
 Start the server
``uv run manage.py runserver``		ou 		``uvm runserver``
ou ``uvm runserver 127.0.0.1:8001``

# Intallation  de wagtail starter kit UV

1. Intaller un environment virtue
   ``uv venv``
 Activé l'enviroment virtuel
 ``source .venv/bin/activate``

2. Installer le paquet startkit
 ``uvx wagtail start --template=https://github.com/wagtail/news-template/archive/refs/heads/main.zip nom_projet . ``

2. Installation des dependance de site starter kit:
 ``uv pip install -r requirements.txt`` 
 
3. Pour migrer les bases des données, collection des data file et .. avec la commande suivante
 ``make load-data``
 ou
```
uvm createcachetable
uvm migrate
uvm load_initial_data
uvm collectstatic --noinput
```

3. **Start the Server**: Start the Django development s
``make start``		ou 		``uvm runserver``

6. On supprimes les fichier qui ne sont pas necessaires dans le projet 