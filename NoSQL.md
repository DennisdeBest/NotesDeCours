#NoSQL

24/10/2016

##Not only SQL
* Ne pas se cantonner à une seule techno (BdD relationelles et non relationelles)
* Problématique Big Data et Clustering
* SGBD

Grosses compagnies et NoSQL :
* Google Bigtable
* Facebook Cassandra
* Amazon Dynamo

Problématique SQL :
* Schéma fixe
* Scalabilité compliqué
* Mécanismes de réplication Master/Slave (un node master et pleins de slaves, requêtes simultanées load balancé -> cohérence de données -> écriture donc que sur master puis répliqués -> lent)
* Language de query complexe pas entièrement exploité

!= NoSQL :
* SchemaLess
* Schéma géré sur le layer applicatif : Modèles sur l'appli
* Migration de données maitrisée : ajouts de colonnes, tables ...

Scalabilité :
* Scalabilité horizontale (ajout de nodes (serveurs))
* Nodes
* Scalabilité automatique (Simplifiée, prévu par NoSQL)

Sharding :
* Découpage de la base en morceaux (+/- Stripping en RAID)
* Scalling horizontale non répliqué
* Fonctionnement par tag (ex: tag par lieu géographique)
* Séparation des données dans plusieurs pays pour un accès plus rapide en local.

Réplication :
* Scaling horizontal
* Pas de master/slave
* L'écriture se fait sur n'importe quel serveur et est ensuite répliquée ou shardée
* LoadBalancing read/write.

Optimisation :
* Requêtes simplifiées (no more JOIN)
* Sotckage de structures simples ou complexes
* Write optimisés
* Très rapide
* Supporte les stream

Inconvénients :
* Query complexes sont difficiles ou impossibles
* Pas de transactions (commit d'une suites de requêtes)
* Pas de "Reférential integrity" : contraintes cascades, foreign key, etc ...
* Pas de "Strong Consistency" : Ecritures des données dans tous les nodes.

> L'objectif de NoSQL est de proposer une solution de stockage de données la plus proche possible des besoins.

##Les principaux types

###Orienté clé valeur
* enregistrement = clé + valeur
* Clé unique
* Valeurs sérialisée
* Pas de tables mais de buckets
* Très utilisé pour le cache
* Pas de recherches sur la colonne valeurs
* Stocké en RAM (+vitesse)

Avantages :
* Performances
* Utilise très peu d'espace
* Très scalable
* Très simple de mise en place
* Date d'expiration

Inconvénients :
* impossible d'extraire en fonction de la valeur
* Update multiple difficile
* Pas la bonne solution pour filtrer ou trier

Examples de bases :
* Redis
* memcached
* OrientDB
* ArangoDB
* Riak
* Berkeley DB
* Azure tablestore
* Oracle NoSQL
* ...

###Orienté colonne
* Chaque colonne est traité individuellement (dans un fichier séparé)
* Array processing (opération sur toutes les valeurs d'une colonne)
* "Row output" si besoin
* Les données des colonnes sont stockées séparément

Avantages :
* Meilleurs performances sur les requêtes que sur qq colonnes
* Réduction I/O
* Comporession très efficace
* Ajouts modifications, supression de colonnes simple et rapide

Inconvénients :
* Transactionnel lent (si présent)
* Ecritures lentes
* Plus lent que SQL pour accèder à des lignes entières selon de colonnes indéxés (ex selection par PK)

Pour quels besoins :
* Analyse rapide
* Statistiques
* Performances de filtrage et de tri analytique
* Big Data
* Très utilisé dans la finance
* Connées similaires dans les colonnes (compression)

Examples  de bases :
* HyperTable
* HBase
* Druid
* Vertica
* Cassandra
* Google BigTable
* Amazon AWS Redshift
* MS SQL Server 2012
* Oracle Database (option In-Memory)

###Orienté documents
* Stockage par documents
* Document = Structure flexible (JSON, BSON, ...)
* Document à des métadonnées : collection, tag
* Filtre et tri sur le contenu
* SchemaLess
* Relationnel (reférentiel)

Avantages :
* Réplication
* Références
* Read/write
* Indexation (+ indexation géospatial)
* Flexible (documents mutables)
* Scalable (sharding)

Inconvénients :
* Pas de JOIN
* Query basiques
* Filtrage applicatif additionnel pour les cas complexes
* Consistency pas garantie

Pour quels besoins :
* Back-end avec des gros volumes read/write
* Back-end familiers avec du JSON/BSON
* Besoins de structures nested
* Besoins de flexibilité (Pas besoin de renseigner tous les champs)
* Prototyping (POC, ...)

Examples de bases :
* MongoDB
* CouchDB
* CoucheBase
* SimpleDB
* RethinkDB
* OrientDB
* ArangoDB
* ...

###BDD graphes
> GraphQL de facebook (langage pour requêter les bdd graphs)

* L'ancêtre des BDD relationelles
* Constitués de nodes et de relations (edges)
* Chaque node et edge peut avoir des propriétés
* Fonctionnement par voisinage
* Accès extrèmement rapide à des données très éloignées (ex: amis des amis qui aiment la même chose que moi)
* Application de la théorie des graphes

Avantages :
* Accès rapides à des noeuds distants
* Recherches complexes
* Compression extreme
* Transactionel

Inconvénients :
* Statistiques et array processing sur des colonnes impossible ou très lent
* Cohérence et scalabilité compliquée

Pour quels besoins :
* Besoins de relations sur différents niveaux
* Lorsque des instances d'entités peuvent être reliées à d'autres instances d'entités (ex: le réseau routier)
* Réseaux sociaux
* Recommandations sur du e-shopping
* Infrastructure systèmes et réseaux
* IA (ex: Akinator)

Quelques bases :
* Neo4j
* OrientDB
* ArangoDB
* Facebook BDD
* Oracle spatial and graph
* ...

##Guide visuel
D'après le théorème de Brewer on ne peux que satisfaire 2 contraintes en même temps.

![Visual Guide](img/nosql/1.png)














