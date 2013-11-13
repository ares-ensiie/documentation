
#Administration des mailing-lists

Cette documentation est une simplification et adaptation de la [documentation](http://listes.ares-ensiie.eu/wws/help/admin) de sympa.

##Demander la création d'une liste de diffusion


Pour demander la création d'une liste de diffusion, procédez comme suit :

   - Consultez la [page d'accueil du service](http://listes.ares-ensiie.eu/wws/home) et connectez-vous.
   
   - Dans le menu supérieur, cliquez sur le lien `Création de liste`.
    
    	Si le bouton n'apparait pas, cela signifie que vous n'avez pas les privilèges nécessaires pour créer une liste.
    
   - Donnez un nom à votre liste (n'entrez que le nom sans l'arobase et le domaine ; exemple : `monexemple` et non pas `monexemple@ares-ensiie.eu`).
   
   	 	N'utilisez pas d'espaces, d'accents, ni de caractères spéciaux dans les noms des listes : ces caractères peuvent créer des problèmes. 
      
   - Choisissez un type de liste parmi les types prédéfinis (`Groupe de travail` est le plus simple, choisissez ce type si vous ne savez pas)
 
   - Saisissez un objet pour votre liste. Ce point n'est pas très important
   
   - Choisissez une catégorie dans la liste déroulante `Catégories`.

    	Si aucune des catégories existantes ne répond à vos besoins, vous pouvez demander la création d'une nouvelle catégorie, ou choisir "Autre".
    	
  - Saisissez une description pour votre liste. Ce point n'est pas très important.
  
  - Cliquez sur le bouton `Envoyer votre demande de création`.

Un message s'affiche alors et vous informe que votre demande de création de liste est enregistrée et que vous pouvez dès à présent modifier la liste en cliquant sur le bouton `Admin`. Il vous avertit néanmoins que la liste ne sera effectivement installée et rendue visible sur le serveur que lorsqu'un listmaster aura approuvé sa création.

Vous devrez ensuite attendre que la création de la liste soit approuvée par l'un des listmasters. Vous recevrez alors un e-mail de notification intitulé 'Création de la liste `nomdelaliste`' vous informant que votre liste a bien été créée.

	Abonnez-vous ensuite à votre liste : la création d'une liste ou le fait d'en devenir propriétaire ou modérateur n'implique pas l'abonnement automatique à la liste !


##Administrer une liste

Pour administrer une liste dont vous êtes propriétaire, procédez comme suit :

   - Allez sur la page d'accueil de l'environnement de listes et connectez-vous.
   
   - Allez sur la page d'information de la liste que vous souhaitez administrer.
   
   - Dans le menu de gauche, cliquez sur le lien `Admin`.

Pour passer d'une section à une autre, cliquez sur le menu de gauche sous l'intitulé `Admin`.

Les différentes sections du module d'administration de la liste vous permettent :

   - de configurer la liste ;
   - de personnaliser les fichiers associés à la liste ;
   - de gérer les abonnés ;
   - de gérer les archives de messages de la liste ;
   - de gérer les erreurs ;
   - de créer, fermer ou restaurer l'espace de stockage partagé ;
   - de supprimer la liste.
   - de renommer la liste ;

Les liens compris dans le sous-menu `Modérer` vous permettent :

   - de modérer les messages envoyés à la liste ;
   - de modérer les documents déposés dans l'espace de stockage partagé ;
   - de modérer les abonnements en attente de validation.

##Configurer la liste

Consultez la documentation de la configuration de listes.
Personnaliser la liste

À partir de cette page, vous pouvez éditer certains fichiers associés à votre liste, parmi lesquels :

   - message de bienvenue : ce message correspond à la notification envoyée aux personnes qui viennent de s'abonner.
   
  - message de désabonnement : ce message est envoyé aux personnes qui se désabonnent de la liste ;
    
   - message de suppression : ce message est envoyé aux personnes que vous désabonnez (commande DEL), notamment parce que leur adresse a généré des erreurs ;
   
   - invitation à s'abonner : ce message est envoyé aux personnes que vous invitez à s'abonner à la liste via la commande INVITE ;
    
  

Par défaut, Sympa utilise des fichiers par défaut ; dans ce cas, le fichier correspondant spécifique à votre liste est vide. Pour modifier un fichier, choisissez-le dans la liste déroulante puis cliquez sur le bouton `Éditer`. Vous pourrez entre autres modifier le champ `From` (expéditeur), le champ `Subject` (objet) et le corps des messages.

	Attention : les valeurs entre crochets sont des variables. Ne les modifiez pas, à moins de réellement savoir ce que vous faites...
	
	
###Gérer les abonnés

La section `Abonnés` vous présente la liste de toutes les personnes abonnées à la liste. Pour chaque abonné, les informations affichées sont :

   - adresse e-mail ;
   
   - domaine auquel appartient l'adresse utilisée pour l'abonnement (@ensiie.fr, @gmail.com, etc.) ;
   
   - vignette si la fonctionnalité a été activée pour la liste ;
   
   - nom (pas toujours affiché : la mention ou non du nom dépend de la méthode employée lors de l'abonnement) ;
   
   - mode de réception des messages ;
   
    
   - date d'abonnement à la liste ;
    
    - date de dernière mise à jour des options d'abonné.

Par défaut, 25 abonnés sont affichés sur chaque page.



Vous pouvez abonner de nouvelles personnes à la liste à partir de cette page :

   - Pour ajouter une seule personne, entrez l'adresse e-mail de la personne que vous souhaitez abonner dans le champ de saisie et cliquez sur le bouton `Ajout`.
     
   - Pour ajouter plusieurs personnes, cliquez sur `Abonnements par lots`. Dans la zone de texte qui apparaît, entrez les adresses e-mail et les noms des personnes que vous souhaitez abonner à la liste (une personne par ligne). Supprimez le texte d'exemple puis cliquez sur `Ajout d'abonnés`.

Si vous souhaitez abonner des personnes sans qu'elles ne reçoivent de notification, cochez la case `Sans prévenir`. Sachez néanmoins qu'il est déconseillé d'abonner des gens sans les prévenir.

Même si vous pouvez abonner vous-même des personnes à vos listes de diffusion, il est toujours préférable que les gens fassent la démarche de s'inscrire eux-mêmes à la liste. Vous pouvez également inviter des personnes à s'abonner à la liste au moyen de la commande INVITE : envoyez un e-mail à sympa en mettant dans le corps du message la commande 
	
	invite nomdelaliste adresseemail
	
Exemple : 
	
	invite bde jean.dupond(@)gmail.com).

Pour accepter ou rejeter les demandes d'abonnement à la liste, cliquez sur `Abonnements en attente`. Vous voyez apparaître la liste des personnes ayant demandé leur abonnement à la liste. Pour accepter ou rejeter une demande, cochez la case correspondant à la personne ayant effectué la demande et cliquez sur le bouton de votre choix.


Pour désabonner des abonnés à partir de cette page, sélectionnez les abonnés en cochant les cases situées en bout de ligne et cliquez sur le bouton `Désabonner les adresses sélectionnées`.

Si vous souhaitez que le désabonnement ne soit pas suivi d'une notification, cochez la case `Sans prévenir`. Il est déconseillé de désabonner des abonnés sans les prévenir, excepté dans le cas où il s'agit d'abonnés en erreur.

Astuce : pour sélectionner tous les abonnés en une fois, assurez-vous tout d'abord qu'ils sont tous affichés sur la page, puis cliquez sur le bouton `Inverser la sélection` : tous les abonnés seront sélectionnés en un clic !

Pour modifier les options d'abonnés d'un abonné, cliquez sur son adresse e-mail.

À partir de cette page, vous pouvez modifier le nom, l'adresse e-mail et le mode de réception des messages de l'abonné. Vous pouvez également le désabonner.

Si l'abonné est en erreur, un second bandeau apparaît sous le bandeau `Information abonné` :

Les informations affichées sont :

   - type d'erreur (en anglais) ;
   - nombre d'erreurs ;
   - période au cours de laquelle des erreurs ont été observées.

Vous pouvez consulter la dernière erreur ou effacer toutes les erreurs. Si vous effacez toutes les erreurs, le score de l'abonné sera remis à zéro.

Pour gérer plus facilement les adresses en erreur, allez à la page `Erreurs` du module d'administration de la liste.

###Gérer les erreurs

Lorsqu'il y a un problème avec les adresses e-mail de certains abonnés (adresses qui n'existent plus, adresses momentanément indisponibles au moment de l'envoi de messages, capacité de la boîte de réception atteinte, etc.), un pourcentage d'adresses en erreur est affiché dans le menu de gauche sous le texte `Taux d'adresses en erreur`. Pour consulter les adresses en erreur, allez à la page `Erreurs` du module d'administration de la liste.

Le logiciel Sympa gère automatiquement les abonnés en erreur : en fonction du nombre d'erreurs et du trafic dans la liste, les abonnés en erreur sont soit notifiés, soit désabonnés, soit leur score est remis à zéro lorsque l'erreur ne se reproduit plus.

Pour faire en sorte que des adresses ne soient plus en erreur, sélectionnez ces adresses en cochant les cases situées en bout de ligne et cliquez sur le bouton `Annuler les erreurs pour les abonnés sélectionnés`. Si l'erreur persiste, les adresses concernées seront de nouveau marquées en erreur lors du prochain envoi de message.

Vous pouvez aussi désabonner les abonnés dont les adresses sont toujours en erreur : un nombre trop grand d'adresses en erreur cause une charge significative sur le serveur de listes. Pour désabonner des abonnés, sélectionnez leurs adresses en cochant les cases situées en bout de ligne et cliquez sur le bouton `Supprimer les adresses sélectionnées`.

	Astuce : pour sélectionner tous les abonnés en une fois, assurez-vous tout d'abord qu'ils sont tous affichés sur la page, puis cliquez sur le bouton 'Inverser la sélection' : tous les abonnés seront sélectionnés en un clic !

###Renommer la liste

Dans le module d'administration de la liste, cliquez sur `Renommer la liste`. Entrez le nom de votre choix puis cliquez sur le bouton `Renommer la liste`. Un message de demande de confirmation s'affiche ; cliquez sur `OK`.

Si vous changez d'avis, il vous suffira d'effectuer la même manipulation pour restaurer l'ancien nom de la liste.

	ATTENTION : lors du renommage d'une liste, vous devez informer les listmasters, sans quoi le changement de nom ne pourra être effectif.


###Supprimer la liste

Dans le module d'administration de la liste, cliquez sur `Supprimer la liste`. Un message de demande de confirmation s'affiche ; cliquez sur `OK`.

Attention : si vous supprimez la liste, vous ne pourrez pas la rouvrir vous-même !!! Si vous désirez rouvrir la liste, il vous faudra faire appel aux listmasters.

Concrètement, quelles sont les conséquences d'une fermeture de liste ?

   - Tous les abonnés sont immédiatement désabonnés de façon automatique (y compris les propriétaires et modérateurs).
    
   - Les archives de messages sont préservées mais plus personne ne peut y accéder.
    
   - Les documents publiés dans l'espace de stockage partagé sont préservés mais plus personne ne peut y accéder.
   
   - Seuls les listmasters ont le pouvoir de rouvrir la liste ; tous les anciens abonnés seront réabonnés automatiquement.

Attention : en raison d'un petit temps de latence, les pages relatives à la liste restent accessibles à quiconque connaît leur adresse pendant un petit moment. Elles deviendront ensuite complètement inaccessibles.

Si vous souhaitez que la liste et tous les fichiers associés soient supprimés définitivement, vous devrez vous adresser aux listmasters.


