# Server Proxmox

https://dns.ouaga.shop:8006/
root
@Mandoulougou12

## Debian server

address 192.168.2.100

``ssh debian``
login: wellby
pass: @Mandou12

sudo su
Pass: @Mandou12


```
Host debian
    HostName dns.iyaar.bf
    Port 2222
    User wellby
```
## Installation de paquet
1. ``sudo apt install git``
2. ``sudo apt install python3-venv python3-dev libpq-dev postgresql   postgresql-contrib nginx supervisor git build-essential curl``

3. ``adduser djangoapp1``
4. ``usermod -aG sudo djangoapp1`` mot de pass: