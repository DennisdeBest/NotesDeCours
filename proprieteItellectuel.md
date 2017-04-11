# Le droit de la propriété intellectuel
10-04-2017

Défendre ses créations au sens large du terme.
Monopole de l'exploitation
CPI : **C**ode de la **P**ropriété **I**ntelectuelle
Protège toutes les oeuvres à partir du moment qu'elle sont **tangibles**, matérialisées (les idées ne sont pas protègeables).

Propriété de l'objet (support) != Propriété de la création (immatériel)

Contrefaçon : Toute utilisation d'une oeuvre sans l'autorisation du créateur (contrat écrit). => 300 000€ d'amendes, 3ans de prison + dommages et intérêts au ayants droits.

## **P**ropriété **L**ittéraire et **A**rtistique
Protège toutes les créations ayants une dimension artistique.
* Droits d'auteur : Monopole d'exploitation d'une oeuvre de l'esprit. 70 ans après la mort de l'auteur. La protection se met en place dès la création de l'oeuvre (pas de dépot, preuve de création notaire/huissier, envoie à soi même d'une copie de l'oeuvre avec accusé de réception, mis en ligne sur internet)
* Copyright n'as aucune valeur en France (c'est les droits d'auteurs anglo saxons et américain, besoin d'un dépôt)
* Droits voisins du droit d'auteur : Droits des auxilières de la création (gens qui participent à la création ex: éditeurs, producteurs, artistes interprètes) 50 ans à partir de la divulgation de l'oeuvre.


## **P**ropriété **I**ndustriel
Protège les créations ayant un but exclusivement industriel et commercial, (apporte un avantage concurentielle à une entreprise).
* Brevets => Inventions / Innovations techno et procédés techno.
pour breveté il faut que ça soit nouveau et possible de le fabriquer industriellement. 20 ans non renouvelable.
* Marquesc : Signe distinctif d'un produit ou d'un service. 10 ans renouvelable
* Dessins & modèles, protège la forme et l'ornémentation du produit (design) (ex: apple/samsung) protégé 5 ans renouvelables 5 fois.
* **A**ppelation d'**O**rigine & Labels, signes distinctifs relatifs à une charte de qualité, des contraintes de productions, indication géographique, même durée et protection que la marque.
* Obtentions végétales : Protection de la création de nouvelles espèces végétales (création pas découverte).

Dépot à l'**INPI** obligatoire.

### Exercice, comment protéger les créations.

* Un scoop journalistique : pas protégeable
* un article de presse : droit d'auteur
* le nom d'un magazine : dépôt de marque
* le site internet : droits d'auteur, marque NDD
* une nouvelle émission télé : Droits d'auteur
* une affiche publicitaire : Droits d'auteurs
* un logo : dépôt de marque, droits d'auteur
* un nouveau concept radio : c'est une idée pas matérialisé donc pas protegable
* une nouvelle montre connecté : Brevets, dessins, marque
* une nouvelle web-serie : Droits d'auteurs
* un reportage vidéo d'information générale : Droits d'auteurs
* nouvelle ligne de vetements : dessins et modèles
* une nouvelle coiffure : Droits d'auteurs
* un nouveau parfum : Dessins et modèles, marques, brevets
* une nouvelle technique de création d'images de synthèse : Brevet, droits d'auteur sur les images
* Une nouvelle méthode de maquillage cinéma : Rien du tout
* un cours de droit de la propriété intellectuel : Droits d'auteurs
* un nouveau logiciel : Droits d'auteurs, pas brevetable
* un nouveau bijou : Droits d'auteurs
* un château de sable : Droits d'auteurs
* une recette de cuisine : Droits d'auteurs
* une interface d'un logiciel : Pas protegable
* Un algorythme : Pas protegable
* une nouvelle couleur: brevet, marque
* un graffiti : Droits d'auteurs
* Nom de domaine : Droits d'auteurs imparfait (actions en concurrence déloyale)

## Etude de cas : Base de données pour une ludothèque

Nous sommes prestataire pour créer une base de données pour une ludothèque qui contient tous les jeux (vidéos et physiques).
La base doit être accessible en interne et depuis l'extérieur (fonction de recherche).

Structure de la base de données : Merise
Implémentation : MySQL (OpenSource) ou Oracle (Propriétaire).
Plan Infra : Serveurs frontaux (2), serveurs back (2), serveur de backup (dump du contenu de la base).
Implémentation : Load balancer entre les frontaux, master-slave pour les backs et un script cron pour les dumps de la base.
