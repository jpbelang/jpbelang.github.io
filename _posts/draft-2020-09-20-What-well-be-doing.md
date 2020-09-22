---
layout: post
title: Le projet.
---

# Présentation du projet

J'ai récemment développé un intérêt pour Typescript. Ça fait plus de vingt ans que je 
developpe en Java (avec quelques escales en C++ et C#). Je voulais me sortir de ma zone de confort et 
ça semblait un bon endroit où aller. J'explore aussi Golang. Mais dans mon élan professionnel, je suis 
plus près de Javascript.

Le projet où j'essayerai d'appliquer mes connaissances sera assez simple, et pour commencer, je 
m'intéresserai principalement au backend, pour limiter la portée du projet.

Donc je vais essayer de développer une petite application avec des outils que j'ai trouvés, certains 
assez utilisés, d'autres moins connus, mais qui me supportent dans ma transition vers TypeScript.

À la base, ce sera une interface REST. Cette interface sera gérée principalement par `express`. Le modèle sera 
géré par `typeorm`. Ce seront les deux gros outils utilisés pour commencer. J'ai deux outils du même projet (`typestack`
) que j'aime bien le `type-validator` et `class-transformer`. On aura la possibilité d'en reparler.

Pour les tests, on utilisera trois outils `jest`, et `ts-mockito` pour les tests unitaires: encore un fois, mes
origines Java apparaissent. Mockito est un excellent outil pour moquer les objets, et la version typescript aussi. Pour 
les tests d'intégration, `supertest`. On ne virera pas fous sur les niveaux de test. On gardera ça simple.

# Premières impressions de typescript

Ce que j'aimais beaucoup dans la syntaxe de Golang, c'est l'idée d'implémentation implicite: proche du duck-typing, ça
fait que l'on s'inquiète pas trop des déclarations et d'implémentations des classes. Si ca ressemble, ca fitte. Ça
évite le développement boilerplate d'adaptateurs. 

Typescript supporte très bien plusieurs de ces concepts : on évite ainsi plusieurs bouts de code qui n'ajoutent pas de
valeur a notre code. En plus, la creation d'objets non-typés de Typescript (héritée de Javascript) est triviale. 
Relativement à Java ca sauve des lignes de code qui sont souvent inutiles et bruyantes. Le problème, à mon avis, 
c'est que ca prend de la discipline pour gérer les raccourcis que l'on pourrait utiliser.  

Java, classes, interfaces.  Typescript classes, interfaces et types.



