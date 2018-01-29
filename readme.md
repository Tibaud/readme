# Principes de base Ruby on Rails

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

Mettons maintenant les noms officiels sur ces étapes (avec leur traduction):

+ votre _commande_ au serveur s'appelle une **requête (request)**: elle est envoyée au serveur hébergement le site via votre navigateur<br>
+ le _commis_ s'appelle un **contrôleur (controller)**<br>
+ la _recette_ est un **modèle (model)** et permet de savoir quoi prendre dans le _frigo_: la **base de données (database ou db)**<br>
+ le _dressage_ s'appelle une **vue (view)**<br>

Rails étant fait de manière organisée, lorsque le gérant du restaurant fera le site de son restaurant, il entrera la ligne de commande

<section>rails new burger</section>

ce qui lui créera le dossier complet d'amorce avec de nombreux dossier dont:
+ controllers (notez qu'il y en a plusieurs en fait, en fonction du plat à faire)
+ models (notez qu'il y en a plusieurs pour les mêmes raisons)
+ db (notez qu'il n'y a qu'une, mais elle contient de nombreuses tables différentes)
+ views (notez qu'il y en a plusieurs car on ne dresse pas un burger comme un dessert)

Il ne restera plus qu'à créer / remplir les dossier en fonction de la carte, déterminée en amont par le gérant du restaurant.

## 3 - <a name="routes"></a>Les routes

Vous vous demandez souvent pourquoi quand le serveur annonce les plats d'une commande il y a toujours un gars qui beugle "OUI CHEF !!!!" en cuisine? C'est à cause de Rails!
En effet, si le mec spécialisé en burger commence à se lancer dans la préparation des frites à l’assaisonnement du _coleslow_, je vous laisse imaginer le bordel. Donc quand le serveur commande un burger, c'est le commis burger qui beugle. Et personne d'autre. Et si personne ne répond, pas de burger. Cruel mais vrai.

Vous vous demandez aussi pourquoi il n'y a pas de chef dans cette cuisine. Et bien si en fait. Le serveur, il apporte juste le papier en cuisine. C'est le chef qui annonce la couleur. Dans Rails, le chef ou va l'appeler **route**.

Voici donc l'huile du moteur, le sel de la soupe, les boules du sapin de noël: le fichier **routes.rb**. Il va interpréter les URL et déterminer quel contrôleur va traiter la demande. Dans les grands restaurants, il peut même charger un contrôleur de la préparation de la viande, un autre de la cuisson etc...

## 4 - <a name="bdd"></a>Les Bases de Données
## 5 - <a name="getpost"></a>GET / POST
## 6 - <a name="migr"></a>Le concept de migration
## 7 - <a name="models"></a>Les relations entre les models des BDD
## 8 - <a name="crud"></a>Les fonctions du CRUD
