#Hébergement d'un site web sur les serveurs d'ARES (non PaaS)

##Base de données
Sur `castel`: si le fichier `mysql.secret` n'existe pas, le créer.

Ensuite:

```
chmod 700 mysql.secret
```

Puis aller sur `chef-server` pour récupérer le mot de passe de bertha.

Enfin, aller dans `ares-dbtools` et faire:

```
sudo ./new_db.sh -t MySQL -u username
```
où `username` est le nom d'utilisateur du bénéficiaire de la base de données, par exemple `unbekandt2011`.

Remarques: 

 - Ce script doit être exécuté en tant qu'administrateur
 - Pour afficher l'aide, lancer le script sans arguments
 - Deux types de bases de données sont actuellement disponibles: MySQL et PgSQL
 - Le mot de passe (généré aléatoirement) est envoyé au demandeur de la base de données par mail automatiquement

##Hébergement web
Se connecter à `cachiri`. Exemple:

```
 ssh heckel2012@cachiri 
```

Puis aller dans le dossier adéquat:

```
cd etc/apache2/sites-available
```


Ensuite, créer le virtual host (VHOST):

```
touch nomDeDomaineDuSite
```

Exemple:

```
touch drinkiit
```


Puis créer le dossier de logs:

```
cd /var/log/apache2
mkdir nomDeDomaineDuSite.iiens.eu
```
Apache créera dans ce dossier les fichiers `error.log` (fichier de logs d'erreur) et `acces.log` (fichier de logs des connexions au site).
Exemple:

```
mkdir drinkiit.iiens.eu
```

Enfin:

```
sudo a2ensite
 
sudo service apache2 reload
```

##OVH

Dernière étape: ajouter le CNAME sur ovh.

Chercher le mot de passe sur la keychain puis aller sur [ovh.com](https://www.ovh.com/managerv3/), se connecter, et faire: 

```
-> Choisir un produit (choisir le domaine en question, par exemple iiens.eu)
-> Domaines et DNS
-> Zone DNS
-> Type CNAME
```

Enfin remplir dans le champ `sous-domaine` le nom de domaine en question, par exemple `drinkiit`.
Dans le champ `destination`, ne rien mettre.

Il peut falloir jusqu'à une heure pour que cette manipulation prenne effet.

##Erreurs
Lorsqu'une erreur survient, il faut faire:

```
cd /var/log/apache2
cat error.log
```
A la fin de ce fichier se trouvent les erreurs les plus récentes.

###Erreurs fréquentes

- Oublier de relancer Apache/recharger la configuration d'Apache:

	```
		sudo service apache2 restart
	```
	ou

	```
	sudo service apache2 reload
	```
- Créer un fichier et non un dossier pour les logs
- Créer un dossier pour les logs ne portant pas le bon nom
