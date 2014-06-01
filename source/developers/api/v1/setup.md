#Intégrer Oauth à son application web

##Enregistrer son application

Il faut aller sur <http://developers.iiens.eu/oauth/applications/new> et remplir les deux champs `Nom` et `redirect_uri`.
Ces informations dépendent de l'environnement (développement/production) et sont expliquées en détail dans la suite.
Une fois le formulaire rempli, on récupère deux codes:

- CLIENT_ID
- CLIENT_SECRET

Ces codes peuvent être vus comme des clés ssh publiques et privées.
En aucun cas CLIENT_SECRET ne doit être divulgué, ce qui implique de ne pas l'inclure dans le code source si celui-ci est disponible à tous.

On les enregistre plutôt dans `.bashrc` ou `.zshrc` en tant que variables d'environnement, sous cette forme:

```bash

#Ares
export CLIENT_ID="blablabla"
export CLIENT_SECRET="blablablablabla"

```

On peut vérifier qu'on y a accès depuis le shell comme cela (peut nécessiter un redémarrage du shell):

```bash

echo $CLIENT_ID
echo $CLIENT_SECRET

```


###Environnement de développement

- Nom: mettre son prénom/nom
- redirect_uri: mettre l'url de développement suffixée par `/auth`, par exemple `http://localhost:3000/auth`

###Environnement de production

- Nom: mettre le nom de l'application, par exemple Oauth-demo
- redirect_uri: mettre l'url finale suffixée par `/auth`, par exemple ` http://dashboard.ares-paas.eu/auth`

##Mettre en place l'authentification
Cette partie n'est pas exhaustive, elle ne montre que quelques exemples.

<hr>

**tl;dr:**

- Login: `/oauth`
- Route `/auth` pour répondre à l'api
- Informations importantes:

  ```json

  {
    authorizationURL: "http://www.iiens.eu/oauth/authorize",
    tokenURL: "http://www.iiens.eu/oauth/token",
    clientID: process.env.CLIENT_ID,
    clientSecret: process.env.CLIENT_SECRET,
    callbackURL: "/auth",
  }

  ```
  
<hr>

###Manuellement

Exemples complets présents [ici](https://github.com/gaultier/oauth-demo) (avec `ares_api`)
 et [là](https://github.com/ares-ensiie/oauth-demo) (sans `ares_api`).


Lorsque l'utilisateur se connecte, on enregistre ses informations dans une variable de session,
et pour chaque page, on vérifie l'existence et la validité de cette variable, pour savoir si l'utilisateur est connecté ou pas.

On peut mettre en place ce systême complètement manuellement
ou bien utiliser le module `ares_api` (pour Nodejs): [ares_api](https://github.com/gaultier/ares_api)

###Passeport (Nodejs)

Exemple complet présent [ici](https://github.com/MaximeHeckel/HarborJS).

Cet exemple utilise une classe `User` qui se trouve dans `app/models/user`, qui peut se résumer à:

```json

{
    local:
    {
        username: String,
        password: String,
    }
}

```

Dans `routes.js`, il faut créer les routes suivantes:

```js

 app.get('/logout', function(req, res) {
    req.logout();
    res.redirect('/');
  });

  //Oauth
  app.get('/oauth',
    passport.authenticate('oauth2'));

  app.get('/auth',
    passport.authenticate('oauth2', { failureRedirect: '/' }),
    function(req, res) {
      // Successful authentication, redirect home.
      res.redirect('/profile');
    });

```

Dans `config/passeport.js`, il faut créer plusieurs fonctions:

- `serializeUser`: enregistre l'id de l'utilisateur dans la base de données
- `deserializeUser`: trouve l'utilisateur dans la base de données à partir de son id
- `userProfile`: acquiert les informations de l'utilisateur grâce à un appel à l'api
- `use`: met en place l'authentification en tant que telle.

Cette dernière exécute une requête à l'api, si l'authentification est réussie,
elle récupère un token valide et les informations de l'utilisateur qui vient de se logger (grâce à la fonction `userProfile`).
Ensuite, si l'utilisateur n'existe pas dans la base de données (première connexion), elle l'y enregistre, sinon elle quitte.

```js

    passport.use(new OAuth2Strategy({
      authorizationURL: "http://www.iiens.eu/oauth/authorize",
      tokenURL: "http://www.iiens.eu/oauth/token",
      clientID: process.env.CLIENT_ID,
      clientSecret: process.env.CLIENT_SECRET,
      callbackURL: "/auth",
    } ,
    function(accessToken, refreshToken, profile, done) {
      User.findOne({"local.username": profile.username}, function (err, user) {
        if(!user || err){
          var newUser = new User();
          newUser.local.username = profile.username;
          newUser.save(function(err){
            if(err) throw err;
            return done(null, newUser);
          })
        }
        else {
          return done(err, user);
        }
      });
    }));

};

```
