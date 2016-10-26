#NoSQL

24/10/2016

[TOC]

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

###Les principaux types

####Orienté clé valeur
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

####Orienté colonne
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

####Orienté documents
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

####BDD graphes
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

###Guide visuel
D'après le théorème de Brewer on ne peux que satisfaire 2 contraintes en même temps.

![Visual Guide](img/nosql/1.png)

25/10/2016

##Redis

> Stocké en RAM, Extensible par script LUA, Nombreaux langages supporté.

####Persistence sur disque
* RDB : Snapshot ram selon intervalles
* AOF : Logs de chaque écriture

####Clustering
* Redis sentinel : Replication Master/Slave
* Redis Cluster : Sharding

####Les clés
* 512Mb max théorique
* Clés < 1Kb (1000 chars) recommandé
* Construire une nomenclature !

####Les valeurs
* valeurs sérialisé
* listes
* ...

> Atomicité : ne pas modifier la valeurs à deux endroits différents pour ne pas se retrouver avec des données incohérents

####Expire & TTL
**EXPIRE (clé) (temps en secondes)**
EXPIREAT -> timestamp unix
PEXPIRE, PEXPIREAT -> en millisecondes
TTL -> lire le TTL restant

###Les types de valeurs

####Listes ordonnées (array)
**RPUSH (clé) (valeur1) (valeur2)** : Rajoute valeur à droite de la liste
LPUSH
**RPOP (clé)** : POP à droite
LPOP
**LRANGE (clé) 0 -1** : Récupère un array de la première à la dernière valeur
**LINDEX (clé) (index)** : Récupère une valeur à un index

> Notions de types sur les valeurs, on ne peut pas faire de RPUSH sur une clé qui à été initialisé avec un set

####Les Sets
**SADD (clé) (valeur1) (valeur2) (valeur3)** : Ajout d'un élément
**SREM (clé) (valeur)** : Supression d'une valeur
**SMEMBERS (clé)** : Récupération des valeurs
**SISMEMBER (clé) (valeur)** : Retourne 1 si la valeur est dans le set

####Les hashes (objet)
**HSET (clé) (clé - valeur 1) (clé - valeur 2)** : Crée un hash qui contient plusieurs coupls clé - valeur
**HINCRBY (clé) (clé - valeur)** : Incrémente une valeur d'une clé du hash
**HGETALL (clé)** : Retourne tous les élements à la suite
**HGET (clé) (clé)** : Retourne la valeur d'un des couples clé-valeur du hash
**HEXISTS (clé) (clé)** : Retourne 1 si la clé existe
**HDEL (clé) (clé)** : Retourne 1 si la clé existe

####Collections
Récupérer les valeurs
**KEYS (regex)** : Retourne tous les utilisateurs, très lent car ça doit vérifier toutes les clés

Stocker les id dans un set
**SADD (clé) (valeurs)** ex SADD users "2145"
Et récupérer les ids du set
**SMEMBERS (cle)** ex SMEMBERS users retourne les ids dans le set
On peut ensuite faire des **HGET (clé récupéré depuis le set ou KEYS) (clé)**

###NodeJS : IORedis

> npm install --save ioredis

Pipeline : permet d'envoyer plusiers commandes à redis en une fois -> gains de perfs 50 - 300%

Date : 26/10/2016

##MongoDB

Orienté documents, grands nombre de langages, OpenSource, Scalabilité, Hautes performances.

Document embedded/nested -> Pas de JOIN -> I/O réduites
Indexation puissante sur plusieurs niveaux

Scalabilité:
* Sharding et tagging
* Haute dispo : replicas et auto-failover
* Scalling automatique

Documents rangés par collection.

###Commandes

**db.(nom de la collection).insert([{objet1}, {objet2}])** : Insert les objets JSON dans la collection et crée la collection si elle n'existe pas.
**db.(nom de la collection).find()** : Récupère tous les documents de la collection, rajouter **.pretty()** pour un affichage plus agréable.
####Filtres
 * **.limit(nombre)**
 * **.skip(nombre)**
 * **.sort({critère: ordre})** : ex .sort({infos.age: -1})
 * **.find({ (clé) : (valeur)})** : ex .find({type:'student'})
 * **.find({ (critère): { (opératuer) : (valeur) }})** : ex : .find({ 'infos.age': { $gt : 25 }})
 * **.find({ (clé) : { $in: [ (valeur1), (valeur2) ]}})** : ex : .find({ type: { $in: ['teacher', 'student']}})

####Opérateurs de comparaison
* **$eq** : equal
* **$gt** : greather than
* **$gte** : greater or equal
* **$lt** : less than
* **$lte** : less or equal
* **$ne** :  not equal
* **$in** : in
* **$nin** : not in

####Opérateurs de comparaison
* **$and**
* **$or**
* **$not**
* **$nor**

Exs :
db.users.find({
type : 'teacher', 'infos.age' : 27
}) (AND)

db.users.find({
$and: [
{type: 'teachers'},
{'infos.age': {$lt 25}}
]
})(OR)

####Autres opérateurs
* **$exists** : vérfie qu'une clé existe
* **$type** : type de la valeur (double, string ..)
* **$mod: [x, y]**
* **$regex**
* **$text** : Recherce dans un champs
* **$where** : Javascript dans la recherche
* **$near** : Proche d'une localisation

####Mises à jours
**db.(collection).update( {(condition)}, { $set: { (clé)-(valeur), (clé)-(valeur)}})**
Pour mettre à jour plusieurs utilisateurs : **{ $multi: true }** ou **db.(collection).updateMany()**
> **.explain()** pour débugger une requête

* **$inc** : incrémente
* **$mul** : multiplie
* **$max** : Prends plus grande valeurs entre celle de la base et celle fournie
* **$min**
* **$rename** : Renomme la clé
* **$set** : Change la valeur
* **$unset** : supprime la clé
* **$currentDate** : Date actuelle

#####MAJ des tableaux
**db.(collection).updateMany({ (clé tableau): {$exists : true }}, { $push: {(clé tableau): (valeur)}, $currentDate: { 'lastModified' : true }})**
* **$push** : ajoute un élément à une liste
* **$pop** : Supprime le dernier éléments (ou premier avec une option)
* **$pull** : Supprime des éléments

####Supression
**db.(collection).remove({(clé): condition})**

###Les relations
Il faut ajouter un couple (clé - valeur) dans le document pour lequels on veut rajouter une relation vers un autre document sous la forme :
**$set : { class_id: ObjectId(objectid)}**.
Pour récupérer tous les documents qui ont une référence vers un certain document on utilise :
**db.(collection).aggregate({ $lookup: { from:'(collection2)', localField:'_id', foreignField: '(collection)_id', as '(collection2)' }})**
Ex : 
```JavaScript
db.classes.aggregate({$lookup:{from: 'users', localField: '_id', foreignField: 'class_id', as:'users'}}).pretty()
```
Aggregation pipeline pour de multiples JOINS
1. Grouper les données **$group : { ... }**
2. Charger les résultats **$lookup: { ... }**
3. Retourner un objet à la place du tableau de résultats **$unwind: { ... }**
4. Limiter aux champs intéréssants **$project{ ... }**

Ex :
```JavaScript
db.users.aggregate([
{
	$group: {
		_id:{_cid:'$class_id'},
		count: { $sum: 1}
	}
},
{
	$lookup: {
		from: 'classes',
		localField:'_id._cid',
		foreignField: '_id',
		as: '_classes'
	}
},
{
	$unwind: {
		path: "$_classes"
	}
},
{
	$project: {
		_id: '$_id._cid',
		name: '$_classes.name',
		count:true
	}
}
])
```

###Les indexes
Optimisation !
**db.collection.createIndex( (key and index type specification), (options) )**





