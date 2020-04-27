# sshjeedom
SSH script Jeedom

Le but de ce dispositif est de pouvoir executer des scripts depuis une machine distante sur Jeedom, afin d'étayer mes propos, je vais executer un script sur mon serveur OctoPi depuis Jeedom.

Le but sera d'automatiser la connexion SSH via le partage de clés privées, puis de lancer une commande sur le serveur distant lui demandant d'executer le script.

## SSH, clé RSA et partage, sur la machine Jeedom

En SSH et en root, je saisi les commandes suivantes,

### Génération de ma clé privée

``` bash
ssh-keygen -t rsa
cd ~/.ssh
ls
```
Si je vois bien apparaitre ces fichiers, c'est que la génération c'est bien passé :

``` bash
id_rsa  id_rsa.pub  known_hosts
```
*id_rsa correspond à la clé privée, id_rsa.pub est la clé public, c'est elle que nous allons transmettre à notre machine distante*

Puis un peu de sécurité avec

``` bash
chmod 400 ~/.ssh/id_rsa
```


### Partage de ma clé privée

Maintenant que nos clés sont générés, partageons la clé privée, pour ce faire, toujours en SSH sur Jeedom

``` bash
ssh-copy-id root@octopi.local
```

Ici, root correspond au nom d'utilisateur de ma session distante, sur la machine octopi.local (à remplacer par une adresse IP, ou un nom d'hôte suivant votre configuration)



