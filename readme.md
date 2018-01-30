# Principes de base Ruby on Rails

![Ruby](http://atelier-agile.ch/ruby-on-rails-logo.png)

Débuter avec Ruby on Rails, ROR pour les intimes, c'est avant tou maîtriser quelques concepts de bases en plus de Ruby. Voici quelques informations qui te seront utiles avec de te lancer tes premiers sites sur des rails.<br><br>

1 - [Site statique ou site dynamique ?](#dyna)<br>
2 - [Le MVC](#mvc)<br>
3 - [Les routes](#routes)<br>
4 - [Les Bases de Données](#bdd)<br>
5 - [GET / POST](#getpost)<br>
6 - [Le concept de migration](#migr)<br>
7 - [Les relations entre les models des BDD](#models)<br>
8 - [Les fonctions du CRUD](#crud)<br>
---
## 1 - <a name="dyna"></a>Site statique ou site dynamique ?
On ne choisit pas entre un site statique et un site dynamique: on en a besoin ou pas! Mais quelle est la différence me direz vous? Elle est extrêmement simple. Comme son l'indique, le critère statique d'une page vient du fait que son contenu est identique pour tous les internautes.

Les sites statiques ne courent plus les rues, la faute à ses maudits users et leur volonté de personnalisation (ou les besoin de ciblage publicitaires du site). Un site dynamique permet en effet d'adapter le contenu d'une page ou d'un site à chaque profil, en tenant compte de nombreux critères. Ces critères sont principalement collectés par 2 canaux:
1 - les cookies (qui permettent le suivi statistique, le retargeting publicitaire, l'authentification et plein d'autres choses)
1 - les bases de données qui contiennent, ô surprise, les données du profil (au choix plein d'infos utiles comme le mail, l'IP, les timestamp de connexion, les préférences propres à chaque site etc...)

Voyons donc maintenant quelques notions techniques utiles concernant Rails.

## 2 - <a name="mvc"></a>Le MVC
MVC, veut dire Model View Controller. Oui. Et même un solide niveau en anglais ne vous permet pas d'en savoir plus. Alors on va décortiquer un peu la bête.

Imaginons que notre user commande un burger au restaurant.
+ vous commandez un burger serveur, qui transmet en cuisine
+ le commis regarde si il a une recette de burger
+ le commis prend ensuite les ingrédients dans son frigo et les prépare
+ le commis fait enfin le dressage afin de vous présenter le plat "comme sur la photo"

![burger](https://assets-cdn.mrhyde.com/app/uploads/2016/07/19144315/win-a-burger-party-at-honest-burgers-5-256x256.jpg)

Mettons maintenant les noms officiels sur ces étapes (avec leur traduction):

+ votre _commande_ au serveur s'appelle une **requête (request)**: elle est envoyée au serveur hébergement le site via votre navigateur<br>
+ le _commis_ s'appelle un **contrôleur (controller)**<br>
+ la _recette_ est un **modèle (model)** et permet de savoir quoi prendre dans le _frigo_: la **base de données (database ou db)**<br>
+ le _dressage_ s'appelle une **vue (view)**<br>

Rails étant fait de manière organisée, lorsque le gérant du restaurant fera le site de son restaurant, il entrera la ligne de commande
```
  // La première ligne de commande
  rails new burger
```
ce qui lui créera le dossier complet d'amorce avec de nombreux dossier dont:
+ controllers (notez qu'il y en a plusieurs en fait, en fonction du plat à faire)
+ models (notez qu'il y en a plusieurs pour les mêmes raisons)
+ db (notez qu'il n'y a qu'une, mais elle contient de nombreuses tables différentes)
+ views (notez qu'il y en a plusieurs car on ne dresse pas un burger comme un dessert)

Il ne restera plus qu'à créer / remplir les dossier en fonction de la carte, déterminée en amont par le gérant du restaurant.

## 3 - <a name="routes"></a>Les routes

Vous vous demandez souvent pourquoi quand le serveur annonce les plats d'une commande il y a toujours un gars qui beugle "OUI CHEF !!!!" en cuisine? C'est à cause de Rails!
En effet, si le mec spécialisé en burger commence à se lancer dans la préparation des frites à l’assaisonnement du _coleslow_, je vous laisse imaginer le bordel. Donc quand le serveur commande un burger, c'est le commis burger qui beugle. Et personne d'autre. **Et si personne ne répond, pas de burger.** Cruel mais vrai.

Vous vous demandez aussi pourquoi il n'y a pas de chef dans cette cuisine. Et bien si en fait. Le serveur, il apporte juste le papier en cuisine. C'est le chef qui annonce la couleur. Dans Rails, le chef ou va l'appeler **route**.

>Le fichier **/config/routes.rb** va interpréter les URL et déterminer quel contrôleur va traiter la demande. Dans les grands restaurants, il peut même charger un contrôleur de la préparation de la viande, un autre de la cuisson etc...

## 4 - <a name="bdd"></a>Les Bases de Données

Retour dans la cuisine. Vous imaginez bien qu'il y a un nombre important de recettes, il s'agit donc d'être bien organisé. Du coup, quand vous demandez un plat, le chef va juste savoir si c'est plutôt _de la viande_ ou _du poisson_, et désigne le contrôleur concerné. Ce dernier va tout faire pour assurer (car il n'aime pas les erreur le chef), et va donc prendre les ingrédients exacts qui correspondent à la recette dans le frigo, avant de réaliser le plat comme indiqué, ni plus ni moins.

Autant dire que le frigo est organisé rigoureusement: le rayon viande, le sous rayon bœuf, le sous-sous rayon côte de bœuf, les côtes de bœuf avec leur poids et leur origine. Pareil pour les poissons, les légumes ...

Imaginez un peu classeur excel qui se mange (sisi, imaginez, c'est top): celà s'appelle une **base de données (database ou db)**. Les différents rayons s'appellent des **tables** et les produits en bout de chaîne des **entrées**, chaque entrée ayant un **identifiant unique**.

La base de données peut être plus compliquée à gérer que votre frigo, car les tables peuvent être liées en elles, et les requêtes très complexe à organiser. La bonne préparation de la structure d'une base de données à de grande répercutions sur les performances d'affichage d'un site et doit être considérée comme prioritaire dans la conception d'un site. **Car si la côte de bœuf arrive froide, le client ira manger ailleurs**.

## 5 - <a name="getpost"></a>GET / POST
Même si ce n'est pas simple, on va tenter de rester dans la restauration. Le serveur revient avec votre plat et vous dit:

voici votre burger avec du pain, du steack, de la raclette, des cornichons, du ketchup ...

Pas cool, car:
+ vous n'êtes pas aveugle
+ votre viande est en train de refroidir pendant cet inventaire

**Ça c'est la méthode GET**, ça se faisait déjà de moins en moins quand tout le monde disait que Google ça ne marcherait pas car il n'y avait pas de photo sur la page d'accueil. Cela consiste à passer des paramètres dans l'URL, et donc visible par tous,y compris les moteurs de recherche, et, pour le référencement, c'est mal quand ça ressemble à ça:

[http://maisonduburger.com/burger.html?recette=pain&steack&raclette&cornichons&ketchup&cuisson=biencuit](#)

**Indigeste!** pas seulement le ketchup avec la raclette, mais visuellement c'est moche, ça ouvre la porte au scraping aisé de votre site par des spammeurs, et en référencement c'est de la daube (je vous prépare un atelier à ce sujet)

![google](https://pakwired.com/wp-content/uploads/2014/09/google-facts-04.jpg?x47252)

Bon attention, la méthode GET a cependant certains intérêts, et principalement le fait de pouvoir être mise en cache, et, avec un peu d'URL rewriting, on retombe sur nos pieds côté référencement

En face, il y a **la méthode POST**. La requête est cette enregistrée et envoyée à la base de donnée, et les paramètres sont dans le body. On peut donc interagir avec la base de données (mise à jour de données par exemple), sans se confronter à la limite du nombre de caractères de l'URL.

>Il faut donc être conscient des objectifs avant de choisir GET ou POST.

## 6 - <a name="migr"></a>Le concept de migration

La carte du restaurant est régulièrement changée, cela implique des changements au niveau des ingrédients, l'intégration de nouveaux produits ou types de produits, répondre à de nouvelles normes... bref **il faut modifier les tables et/ou les entrées**.

>Avec Rails, il existe plusieurs commandes pour gérer sa base afin de ne pas y passer des jours (comme c'était le cas il y a 1000 ans avec des sites qui tournaient avec une base access), puis de migrer (faire une **migration**) ces données afin de pouvoir les utiliser.

  ```
  //easy game la migration:
  db:migrate
  ```

## 7 - <a name="models"></a>Les relations entre les models des BDD

Vous avez peut être fouillé dans le frigo d'un ami sans pouvoir rien y trouver. Normal, il a organisé son frigo selon ses habitudes ou ses besoins. Même si son rangement est moins bon que le votre (forcement), considérez qu'il a peut être raison. Car il existe plusieurs manières d'organiser une base de données.

Retournons au restaurant, et parlons viande d'autruche. Il y a plusieurs manière de mettre CE steack d'autruche dans la base:
+ une table viande avec toutes les entrées dont notre steack qui a de nombreux paramètres (animal, partie de l'animal, poids, origine, DLUO ...)
+ une table viande, plusieurs sous tables (animal, origine, partie de l'animal), et enfin l'entrée qui contiendra des critères dont certains renvoient à d'autres tables

Le premier type d'organisation, **orienté objet**, peut faire l'affaire lorsqu'il y a peu de data. Le second, dit **méthode relationnel**, permet d'avoir des recherches beaucoup plus rapides car filtrées.

Je m'explique. Imaginons que vous cherchiez un steack d'autruche de 250 grammes (oui, tu as faim). La première méthode va aller regarder TOUTES les entrées de la table viande. Même celles qui sont du poulet ou de l'agneau. Avec une base sur la méthode relationnel, la requête ne va consulter que les entrées qui appartiennent aux tables viande ET autruche ET steack afin de trouver les morceaux dont le poids est 250 grammes.

>La méthode relationnel est plus complexe à mettre en place, mais bien plus efficace quand on a beaucoup de critères pour une entrée.

Pour en revenir à Rails, le modèle déterminé par le contrôleur va générer une requête en base, qui sera différente en fonction de la méthode d'organisation de la base.

## 8 - <a name="crud"></a>Les fonctions du CRUD

CRUD, pour le coup, c'est parlant même pour les nuls en anglais: cela permet d'intéragir avec la base de données afin d'appliquer les actions suivantes:<br>
Create pour créer un élément (en utilisant POST)<br>
Read pour lire un élément (en utilisant GET)<br>
Update pour mettre à jour (en utilisant PUT)<br>
Destroy pour le supprimer (en utilisant DELETE)

___

Feel free to share - with love by @TIbaud
