# Déployer son application sur ares-paas.eu

Cette documentation a pour but de vous guider lors de votre premier déploiement d'application sur le PaaS ( Plateform as a Service ) de l'école.


## S'authentifier auprès du serveur

Afin de garantir la sécurité de vos applications, il faut vous authentifier auprès du serveur à l'aide d'une clé ssh. Pour se faire il vous faut [générer les clés privée et publique](https://help.github.com/articles/generating-ssh-keys) sur votre machine, et ensuite envoyer votre clé publique sur le serveur ares-paas.eu.
La saisie de nouvelle clé ssh demandant l'accés root au serveur hébergeant les applications du PaaS, nous vous demanderont de bien vouloir envoyer cette clé publique à ARES en attendant que le dashboard du PaaS soit fonctionnel, ou que l'on trouve une solution vous permettant de le faire vous même.
Une fois cette étape réalisée, votre machine sera référencée sur le PaaS et vous autorisera à déployer votre application.

## Préparer son application

Tout d'abord, il est nécessaire que votre application soit dans un répository Git et qu'elle soit à jour. Si ce n'est pas le cas :

	git init
	
	git add -A
	
	git commit -m "Ready to deploy"
	
**Attention**

Certaines technologies, comme Node.js par exemple, nécessitent un fichier additionnel au projet afin de garantir le bon fonctionnement de votre application lors du déploiement : le Procfile.
Un Procfile est un petit fichier vous permettant de déclarer la commande à éxécuter pour lancer votre application lors du déploiement. Si votre application nécessite un Procfile, vous pouvez les trouver facilement sur internet ou plus précisement sur la documentation de Heroku.


Il vous faut ensuite ajouter le **remote** de ares-paas.eu à votre projet :

	git remote add ares dokku@ares-paas.eu:NOM_DE_VOTRE_APP
	
Vous êtes maintenant prêt à déployer votre application.


## Déployer son application

Vous n'avez beson que d'une seule commande :

	git push ares master
	
Votre application va être pushée sur le serveur, reconnu et installée par le PaaS. A la fin du déploiement, vous pourrez observer une URL de la forme [NOM_DE_VOTRE_APP.ares-paas.eu](), il s'agit tout simplement du lien vers lequel vous pouvez accéder à votre application.

Vous venez de déployer votre première application sur ares-paas.eu ! 
