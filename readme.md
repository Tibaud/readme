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

Imaginons que notre user commande un burger au restaurant. Il demande au chef de le lui préparer. Que se passe t'il ensuite ?
+ - le chef regarde si il a une recette de burger
+ - le chef prend ensuite les ingrédients dans son frigo et les prépare
+ - le chef fait enfin le dressage afin de vous présenter le plat "comme sur la photo"

Mettons maintenant les noms officiels sur ces étapes (avec leur traduction):

+ votre _commande_ s'appelle une **requête (request)**: elle est envoyée au serveur hébergement le site via votre navigateur<br>
+ le _chef_ s'appelle un **contrôleur (controller)**<br>
+ la _recette_ est un **modèle (model)** et permet de savoir quoi prendre dans le _frigo_: la **base de données (database ou db)**<br>
+ le _dressage_ s'appelle une **vue (view)**<br>


## 3 - <a name="routes"></a>Les routes
## 4 - <a name="bdd"></a>Les Bases de Données
## 5 - <a name="getpost"></a>GET / POST
## 6 - <a name="migr"></a>Le concept de migration
## 7 - <a name="models"></a>Les relations entre les models des BDD
## 8 - <a name="crud"></a>Les fonctions du CRUD
