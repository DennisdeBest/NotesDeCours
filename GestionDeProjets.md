#Gestion de projet

Date: 10/10/2016

##Les grandes parties
* ITIL -> DSI
* SCRUM -> agile
* ISO 9001 -> norme de qualité

##OneNote class

Exercise : YYYY-MM-DD_E1-Acronyme
Trouver un mot pour chaque lettre de son nom.
**N**amaste
**O**urangoutang
**M**alade

Exercise 2 : Origine du QQOQCCP (3 lignes)
Comment on l'utilise, quel intérêt ça représente pour nous (5 lignes)

##Cycle de vie SI

###Acteurs et métiers

> **P**lan **D**o **C**heck **A**ct
(Roue dites de Deming dans ISO 9001)

**PLAN** Définition des besoins (software/hardware) qui ? quoi ? quand ? pourquoi ? combien ? comment ?
**DESIGN** Définitions des specs fonctionels
**BUILD** Phase de développement
**RUN** TMA corrective, évolution, adaptative, perfective - Infra **M**aintenance en **C**ondition **O**perationel

> Ex : Renault => Vend des voitures
> Processus (ensemble d'actions corrélés ou interactives qui transforme quelque chose) :
> 1. **Commerce**
> 2. **Production**
> 3. **Comptable**
> 4. Publicité / Marketing
> 5. R & D
> 6. RH
> 7. Logistique
> 8. Qualité
> 9. Service après vente
> 10. Juridique / Propriété intellectuele
> 11. SI
> 12. Financier (créer une plus-valus)
>
> Cycle de vie du métier commerce :
> * P :
>     * qui ? direction métier, DSI, Direction Financière
>     * pourquoi ? Acien système inéfficace
>     * quoi ? **C**ustomer **R**elation **M**anagement
>     * quand ? urgent
>     * combien ? +20% de ventes (direction commercial) 100 000€ (DSI +/-)
>     * comment ? OpenCRM
> Determination d'une **cible**, d'une **charge** et d'un **délais** -> un **projet**
> * D : Définition des specs fonctionel
> * B : Développement en respectant les spects, lancement
> * R :
>     * TMA
>     * MCO

Date : 11/10/2016

Exercise: 2016-10-11_E3-Chaos_Report à faire pour le 24/10/2016
[Standish group](https://www.projectsmart.co.uk/white-papers/chaos-report.pdf), société de conseil anglaise, produit une étude, le "chaos report". Référence de plus de 1000 projets informatique classés en 3 catégories :
* Délais, charge, cible réalisé
* Un ou deux paramètre pas réalisé, livré en retard
* Abandonné
Faire une synthèse critique, es ce que les projets sont représentatifs, es ce que les petits projets/start ups sont pris en compte dans ces études.

2016-10-24_E4_Plan
Finir le plan de la DSI, personne en interne pour faire des estimation, personne pour faire du dev, lancer un appel d'offre aupreès de plusieurs sociétés (Cap gemini, Cgi, ...), présenter ces offres.

####Distribution des rôles
Plan :
* MOA : DG, DF, DMétier
* MOE : DSI

Design :
* MOA : DSI
* MOE : SSII, Construteurs

##Methodes de gestion de projet
**Traditionel** ou **Agile**

---
Date : 24/10/2016
A faire pour la prochaine fois:
Corriger  le chaos report de (note sur 5):
* Deschamps Lea
* Dessombs Thomas
* Estrach Quentin

> **F**acilities **M**anagement (élec, clim, télécom ...)

Un processus projet doit àvoir une charge et un délai.
Ex Etchebest et le rougail saucisse, un beau matin fifou tombe sur une recette de rougaile saucisse.
En **Plan** Il réunit les chefs, la DG et ils brainstorment sur la *stratégie* (pourquoi ?, quand ?, qui?, quoi ?)
Une fois la stratégie établit et validé la phase **Design** consiste à rechercher des recettes, faire des essaies, du *prototypage* (comment ?, combien ?, quoi ?).
La phase **Build** sert à industrialiser le prototype, qui fait quoi quand en combien de temps ? On rajoute le plat sur la carte etc ...
**Run** : si quelqu'un commande un réalise le processus définit à la phase précédente, traiter les éventuels retours.

Faire les phase design et build par groupe de deux, se mettre à la place de HP qui à était choisit par la direction générale des impôts pour faire la platforme infra-réseaux (firewealls, switch, load balancers ...) dans les locaux de la cité administrative pour le 1er mars 2017 (date d'ouverture de la campagne de déclaration des impôts sur le revenue).
20 millions d'utilisateurs avec des pics d'accès de 100 000 utilisateurs en simultané. Faire un design et un POC.

Faire donc deux dessins, un pour le prototypage et un pour l'implémentation.






