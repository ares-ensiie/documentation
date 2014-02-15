#Héberger un site web

Chaque utilisateur d'ARES bénéficie de son espace web à l'adresse `http://ares-ensiie.eu/~IDARES` (remplacer IDARES par votre identifiant ARES). Il ne s'agit pour l'instant que d'un hébergement mutualisé PHP qui couvre la plupart des besoin des utilisateurs.

Pour ce faire, il faut créer dans son dossier personnel les fichiers que l'on veut rendre accessibles sur internet. L'url d'un fichier représente son arborescence relative dans votre dossier personnel.

##Droits
Il n'est pas nécessaire d'autoriser la lecture/écriture/exécution de ces fichiers pour d'autres groupes que soi-même.

Typiquement, `700` suffit.

##Exemple 
Pour l'utilisateur `kevin2020`:

`~/mon_site_web/biere/heineken.php` sera accessible à l'url: `http://ares-ensiie.eu/~kevin2020/mon_site_web/biere/heineken.php`.

Il vous est ensuite possible de louer un nom de domaine et de nous demander de faire la redirection.
Cet hébergement ne fonctionne que pour les sites statiques. Si vous voulez héberger votre site non-statique, vous pouvez utiliser le PaaS.

##Base de données
ARES ne fournit pas encore une base de donnée à tout les utilisateurs, mais il est possible d'en [demander une](/guides/bdd).


