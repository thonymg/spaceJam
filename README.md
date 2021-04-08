# spaceJam (preview)

![SpaceJam logo](https://github.com/thonymg/spaceJam/blob/main/img/logo.png "SpaceJam logo")

> Exténués. Les usagers le sont. Furieux, ils ne le sont pas moins, face à la situation actuelle à Antananarivo en matière de circulation.
« C’en est trop ! », lance-t-on un peu partout, quand les véhicules restent immobiles pendant plus d’une heure, ou que les usagers mettent deux heures, voire davantage pour parcourir moins d’un kilomètre. C’est le cas dans toutes les sorties de la ville, notamment à Ampitatafika vers Anosizato ou en sens inverse. La situation est similaire à Andravoahangy, Ankorondrano, aux 67ha, à Faravohitra, à Behoririka, Analamahitsy, ou encore sur la route circulaire, bref, partout. Il ne faut pas attendre les « heures de pointe » pour le vivre, dans la mesure où le ralentissement de la circulation est visible dès les premières heures de la journée, parfois dès 6h dans certaines zones.
… Le problème de circulation est-il alors sans solution pour la capitale ? Pour l’instant, les efforts déployés par les agents de police de la circulation ne sont pas couronnés de grands succès sans mettre en doute leur bonne volonté, car sans les agents de police postés sur les carrefours et les croisements.

http://www.midi-madagasikara.mg/societe/2019/01/16/embouteillages-a-antananarivo-probleme-sans-solution/


Le projet SpaceJam a pour objectif de réduire les embouteillages dans la capitale (et partout ailleurs) en identifiant les points de blocages et les meilleures solutions possibles via des simulations par ordinateur. Et compte tenu du budget de la capitale, les solutions que nous proposerons seront les moins couteuses possibles. 

Space Jam est simple dans son fonctionnement et suis les étapes suivantes :

-	L'identification de la zone à traiter (il est possible de simuler l’intégralité de la ville, mais nous n’avons pas les moyens, ni le temps, ni la puissance de calcul pour le faire)
-	Prendre des photos/cartographies satellites de la zone. 
-	Retracer les trajets routiers sur notre simulateur. 
-	Entrer les données relatives à la densité de la circulation et de la population dans la zone
-	Lancer le simulateur     
-	Analyser les données de sorties 
-	Relancer le simulateur avec autant de scénarios que nécessaire. 
-	Reanalyser et comparer les données
-	Identifier le meilleur scénario possible.  

### Pourquoi/comment un simulateur ? 
-	Le simulateur nous est venu naturellement compte tenu du fait qu'on n’a aucune autorité sur le réseau routier de la ville. Donc on ne peut pas couper ou orienter le flux de véhicule circulant dans la capitale surtout dans les heures de pointe.  
-	On a besoin de comparer les données avec des indicateurs précis afin de valider ou d’invalider les scénarios
-	On a besoin que les paramètres entre les différents scénarios soient strictement les mêmes. 
-	Dans d’autres domaines scientifiques, la simulation est une étape essentielle avant l'expérimentation, dans l’aérospatiale elle sert même d’entrainement aux conditions réelles. 

### Méthode
Pour avoir des données comparables il est important que les paramètres entre les différents scénarios, soit strictement les mêmes.

## Paramètres de simulation :
Nombre de véhicules : 5400

Durée de la simulation : 5600s

Flux de piétons : 16 à intervalle de 3,5 secondes à des positions semi-aléatoires sur le parcours.

Les piétons causent un ralentissement, moyenne de 70% de la vitesse des véhicules à proximité, et peuvent même causer l’arrêt total du flux de circulation en cas « d’accident ». 
Chaque seconde la simulation nous aurons des données sur l’état courant de la circulation. Ces indicateurs sont les suivantes : 
-	L'émission de CO par seconde par véhicule. 
-	L'émission de CO2 par seconde par véhicule. 
-	L'émission de NOx par seconde par véhicule. 
-	L'émission de PM par seconde par véhicule. 
-	La distance parcourue par seconde par véhicule.

Chaque type de véhicule a un niveau d’émissions de gaz différents, mais les membres du même type ont tous le même la même quantité de gaz émis par seconde. 

Un véhicule sorti de la simulation (qui arrive à destination) n’émet plus de gaz dans l'atmosphère, par contre un véhicule a l’arrêt continue d’émettre à des niveaux plus faibles. Ceci est important, car cela veut dire qu’une réduction de x% dans l’émission de gaz ne correspond pas à une réduction de x% des véhicules à l’arrêt (ou dans les embouteillages). 

Nous garderons donc comme indicateur de performance le niveau d’émission de gaz, plus facilement quantifiable   

### Scénarios
Étant donné que nous sommes sur simulateur, nous avons mis en place plusieurs scénarii afin de trouver la meilleure configuration routière possible. Les scénarii imaginés (pour le moment) ne nécessitent aucun investissement en infrastructure (ou très limités). Donc si un des scénarii est le plus performant en simulation, il est tout à fait possible pour la commune de le mettre en place sans attendre afin de vérifier la performance.

## Cas concret 
Dans notre démonstration, nous avons mis en simulation un axe très célèbre pour ces énormes embouteillages et cela depuis des années : L'axe Analamahitsy. 

Analamahitsy est le point de tension de plusieurs flux à grande circulation venant d’Ivandry, Ambatobe, Nanisana, Massay et Amboditsiry. 

La simulation se fera de manière suivante : 

-	Génération des 5 400 véhicules de manière semi-aléatoire. 
-	Les véhicules ont pour point de départ possible : Ivandry, Ankorondrano, Ampasapito, Ambohitrarahaba, Ambatobe, Androhibe et Analamahitsy. La répartition du nombre de véhicules sur ces points de départ se fait de manière semi-aléatoire. Avec une différence qu’ordre de 12% à 20% pour entre chaque point de départ.
-	Les véhicules ont pour point d’arrivée les quartiers précédemment cités. Mais cette fois avec une différence d’ordre de 22 à 38% quant à la répartition du nombre de véhicules selon le point d’arriver. 
-	Chaque véhicule prendra le chemin le plus court possible pour atteindre sont objectif, indépendamment de la performance de ce trajet.

![map](https://github.com/thonymg/spaceJam/blob/main/img/map.png "map")

### Le scénario contrôle  
Le scénario contrôle représente l’état actuel de la circulation. Elle reprend à l’identique (ou presque) les configurations routières qui sont en place à Analamahitsy. Ce scénario nous servira par la suite de base comparaison avec les autres scénarios où on modifie les configurations routières. 
Il est à noter que nous n’avons pas implémenté « le comportement égoïste » des usagers de la route, que ce soit les bus, ou les motos, plaque rouge trop pressée, ou autres. Car nous pensons qu’il faut une autre simulation spécifique à ces « comportements égoïstes » pour trouver la solution. Nous savons que ce comportement influe de manière significative la performance du flux de véhicules.  
À titre indicatif, un bus qui se gare mal à l’arrêt impacte d’au moins 16% la performance de l’ensemble du flux de véhicule. Et ce n’est pas le seul qui influence la performance du flux. 

##### debut de simulation
![fjkm](https://github.com/thonymg/spaceJam/blob/main/img/control_f/FJKM.gif "fjkm")

![masay](https://github.com/thonymg/spaceJam/blob/main/img/control_f/MASAY.gif "masay")

![total](https://github.com/thonymg/spaceJam/blob/main/img/control_f/TOTAL.gif "total")

##### fin de simulation
![fjkm](https://github.com/thonymg/spaceJam/blob/main/img/control_b/FJKM.gif "fjkm")

![massay](https://github.com/thonymg/spaceJam/blob/main/img/control_b/MASAY.gif "massay")

![total](https://github.com/thonymg/spaceJam/blob/main/img/control_b/TOTAL.gif "total")


### Scénario 1
Le scénario 1 présente quelques changements par rapport au scénario contrôle. On a décidé de rediriger tous les véhicules venant d’Ivandry traversant Analamahitsy vers le rondpoint du Massay. Ce scénario a été discuté au sein de la commune à une certaine époque, mais fut abandonné à cause des manifestations des bus qui desservent la zone.

“Carte”
### Scénario 2
Le scénario 2 consiste en une modification totale du sens de la route de Nanisana et d’Ambatobe. En effet dans ce scénario nous avons décidé de changer la route vers la monter d’Ambatobe depuis la station essence à Analamahitsy en sens unique qui ne servira qu’à monté à Ambatobe, pas de descente donc. Et la route de Nanisana vers Analamahitsy en sens unique vers Analamahitsy uniquement. La descente depuis Ambatobe se fera depuis la route partant du rondpoint Ambatobe vers Nanisana. 

### Scénario 3

Le scénario 3 ne diffère du scénario contrôle que sur la gestion des cycles de passages, et la mise en place d’une deuxième voie sur la rue qui relie la station essence Total et la pharmacie d’Avaradrano. En théorie cette route peut accueillir 2 voitures en parallèle, mais sont état, les voitures mal garées dessus en fait que cette route est sous-exploitée. 

##### debut de simulation
![fjkm](https://github.com/thonymg/spaceJam/blob/main/img/sc3_f/FJKM.gif "fjkm")

![masay](https://github.com/thonymg/spaceJam/blob/main/img/sc3_f/MASAY.gif "masay")

![total](https://github.com/thonymg/spaceJam/blob/main/img/sc3_f/TOTAL.gif "total")

##### fin de simulation
![fjkm](https://github.com/thonymg/spaceJam/blob/main/img/sc3_b/FJKM.gif "fjkm")

![masay](https://github.com/thonymg/spaceJam/blob/main/img/sc3_b/MASAY.gif "masay")

![total](https://github.com/thonymg/spaceJam/blob/main/img/sc3_b/TOTAL.gif "total")

## Résultats 

Nos indicateurs de performance seront le volume des gaz émis et la distance parcourue par l’ensemble des véhicules dans chaque simulation. 

L'Émission de gaz étant fortement liée à l’activité d'un véhicule, la comparaison des taux de chaque simulation nous permet de savoir/comparer l'intensité des embouteillages. Plus le taux est élevé, plus il y a de véhicules bloqués dans les embouteillages.

La distance parcourue nous informe aussi sur l'intensité des embouteillages, plus la distance parcourue est grande, plus la circulation est fluide, moins l’embouteillage est intense.  

En somme le scénario le plus performant est celui avec le moins de gaz émis et plus de distance parcourue sur l’ensemble de la simulation.

| -  | contrôle  |  scenario 1  |  scenario 2  |  scenario 3   | unit | 
| ------------- | ------------- |  ------------- | ------------- |  ------------- | ------------- |
| distance |  14 471,97  |  6 529,06  |  8 857,10  |  15 345,73  | km
| co |  239,53  |  797,44  |  581,32  |  163,35  | kg
| co2 |  10 257,42  |  20 576,89  |  16 452,34  |  9 070,32  | kg
| hc |  9,57  |  29,51  |  21,54  |  6,56  | kg
| nox |  58,68  |  121,85  |  96,74  |  52,95  | kg
| pmx |  2,20  |  5,77  |  4,35  |  1,76  | kg
| loaded vehicle |  5 400,00  |  5 400,00  |  5 400,00  |  5 400,00  | - | 
| departed vehicle |  4 820,00  |  3 395,00  |  3 836,00  |  4 951,00  | - | 
| running vehicle |  1 031,00  |  2 215,00  |  1 768,00  |  563,00  | - | 
| arrived vehicle |  3 789,00  |  1 180,00  |  2 068,00  |  4 388,00  | - | 
| avg speed |  1,64  |  0,11  |  0,29  |  4,75  | m/s


Selon notre simulation le scénario 3 est la meilleure des 3 et bien plus performant que le scénario contrôle.

## Pourquoi est autres scénarios sont moins performant ? 
### scénario 1 : 
Dans le scénario un une redirection des flux vers le rondpoint du Massay permettrait de fluidifier la monté des véhicules sur la partie du FJKM. Pr contre elle augmenterait la pression sur le goulot d’étranglement qu’est le rondpoint Massay en ajoutant une source supplémentaire de flux de véhicule.
### Scénario 2 : 
Ici c’est le flux venant de Nanisana qui pose problème vu qu’on augmentera fortement la pression sur la montée du FJKM. La sortie vers Ambatobe étant postérieur à la monter double sens de Nanisana, cette sortie ne libèrera pas la pression sur la montée. 

## Pourquoi le Scénario 3 est le meilleur ?
Nous avons vu que les autres scénarios impliquant de nouveaux tracés ne sont pas plus performants que le scénario contrôle (en tout cas pour ce cas précis). L’objectif est alors de comprendre, le scénario contrôle, et de l’optimiser le plus possible.   

Dans la simulation nous avons pu déterminer les sources des embouteillages et avons appliqué les modifications nécessaires pour le rendre plus performant. 

-	La file qui passe par le bassin d’Analamahintsy est l’indicateur principal du blocage possible. En effet il faut faire en sorte que cette file ne soit pas bloquée pour garantir une fluidité de ceux qui arrivent Ambohitrarahaba, et ceux qui descendent d’Ambatobe.
-	Nous avons aussi mis un agent de circulation sur le point de rencontre entre ceux venant du Coliséum et ceux venant du Massay. Cet agent régule la circulation en laissant passer 80secondes ceux venant du Massay, contre 50secondes seulement pour ceux venant du Coliséum. 
-	Deux autres agents ont été mis à la jointure avec Nanisana et à la jointure avec Ambatobe. Avec cette fois une configuration plus équilibrée ou dépendant du contexte. 
-	Nous avons aussi imposé le double file sur la route entre la station Total et la Pharmacie. Mais cela n’a de sens que si cette route ne se retrouve jamais bouchonnée

## Limite 
### Technique : 
- Ubuntu 18.4
- Intel core i7-6700HQ
- 16 Go de RAM
- SSD 512 Go

Avec cette configuration nous n’avons pu simuler et analyser qu’une partie de la ville. Les données de chaque scénario ont une moyenne de 1 Go soit à peu près 3,6 millions de lignes. Pour simuler, l'intégralité de la ville nécessiterait des machines avec des puissances de calculs largement supérieures. 
La cartographie satellitaire que nous avons utilisée manque de précision. Certains aménagements ne sont pas pris en compte et d’autres sont mal représentés. C’est notre connaissance du terrain qui nous a permis de distinguer le vrai du faux. De plus cette cartographie satellitaire ne représente pas l’état des routes. Une cartographie via des drones serait plus précise et plus à jour.  

### Limite de données  
La limitation principale que nous avons rencontrée est la limite en termes de données. 
-	Aucune donnée (et aucune source officielle) ne nous a permis de savoir la répartition exacte des voitures en heure de pointe, d’où le choix de la répartition semi-aléatoire.
-	Aucune donnée sur les trajets exacts des bus et leurs points de stationnement précis ni sur le nombre de bus desservant une zone.
-	Aucune donnée sur les écoles dans la zone et leurs heures d’entrée/sortie
-	Aucune donnée sur le nombre exact d’habitants possédant un véhicule par zone
-	Aucune source de donnée sur le nombre d’entreprises sur chaque zone et leurs heures d’entrée/sortie
-	Aucune donnée sur l’état réel des routes.
…	 
Bref la principale faille se situe au niveau des données 

## Dépassement des limites
Il est clair que pour avoir des simulations qui se rapprochent possible de la réalité, il faut les données de la réalité. Pour certains ces données sont tout bonnement impossibles à se procurer. Mais cela ne nous empêche pas de récolter les données qu’il nous faut.
### Comptage des voitures et des piétons.
> LE COMMISSARIAT DU 8EME ARRONDISSEMENT D’ANTANANARIVO SIS A ANALAMAHITSY VIENT DE S’OCTROYER UN CENTRE DE TELESURVEILLANCE. 

La combinaison des images du centre de surveillance et d’images aériennes couplé à une I.A (même des plus basiques) de reconnaissance d’images serait suffisante pour compter les véhicules dans la zone concernée.

Le cas des bus pouvant être l'objet d’autre simulation, il n'est pas absurde de repenser leurs stationnements et leur trajet à ce moment-là.

Quant aux heures de sorties, rien n'empêche la commune de proposer aux écoles des heures de sorties plus favorables à la circulation. 

## Possibilités

Il nous est possible de simuler bien d’autres choses que les embouteillages. Et le besoin que nous jugeons le plus important que nous sommes entrain d’analyser actuellement c’est la simulation des zones de marché. Nous sommes entrain de réfléchir sur comment améliorer 

comme nous l’avons cité précédemment avec la puissance de calcule nécessaire il serait tout à fait possible de simuler le flux dans la ville entière. Cela procurera un bon nombre d’avantages tant à la fois dans la gestion de la circulation, que dans la gestion des agents sur terrain.   

Simulation de la ville entière avec:
- Trajet selon heures/jours.
- Gestion plus efficace des marchés et des foules.

paix et guerison


