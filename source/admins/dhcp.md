#Changer les règles du dhcp

*Une bonne pratique est de prévenir les utilisateurs qu'ils peuvent être déconnectés lorsque le serveur dhcp est redémarré et d'indiquer la tranche horaire.*

Il faut se connecter sur la machine hôte, en l'occurence [Choucroute](http://doc.ares-ensiie.eu/admins/servers/choucroute/):

```
ssh mon_identifiant@choucroute.ares -p 2200
```

Puis en tant qu'administrateur il faut éditer le fichier de configuration:

```
sudo vim /etc/dhcp/dhcpd.conf
```

I faut mettre les règles à l'intérieur des accolades de la section 

```
subnet 10.3.0.0 netmask 255.255.254.0 {
…
}
```
qui est le réseau principal Ensiie.

Puis ne pas oublier de relancer le serveur pour que les règles prennent effet:

```
sudo service dhcp restart
```


