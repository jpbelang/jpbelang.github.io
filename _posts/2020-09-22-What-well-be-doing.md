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

Pour les tests, on utilisera trois outils `jest`, et `ts-mockito` pour les tests unitaires : encore une fois, mes
origines Java apparaissent. Mockito est un excellent outil pour moquer les objets, et la version typescript aussi. Pour 
les tests d'intégration, `supertest`. On ne virera pas fous sur les niveaux de test. On gardera ça simple.

Ah oui, j'oubliais : kossé qu'on va faire. On va faire un système de gestion de cours. Des cours, des profs, des
usagers, des factures...  

# Premières impressions de Typescript

Ce que j'aimais beaucoup dans la syntaxe de Golang, c'est l'idée d'implémentation implicite: proche du duck-typing, ça
fait que l'on s'inquiète pas trop des déclarations et d'implémentations des classes. Si ca ressemble, ca fitte. Ça
évite le développement boilerplate d'adaptateurs. 

Typescript supporte très bien plusieurs de ces concepts : on évite ainsi plusieurs bouts de code qui n'ajoutent pas de
valeur a notre code. En plus, la creation d'objets non-typés de Typescript (héritée de Javascript) est triviale. 
Relativement à Java ca sauve des lignes de code qui sont souvent inutiles et bruyantes. Le problème, à mon avis, 
c'est que ca prend de la discipline pour gérer les raccourcis que l'on pourrait utiliser.  

# Les types : mes débuts

À part les types de base de Typescript, qui sont simples et assez standards, il y a trois façons de créer des types
: Les `class`, les `interface` et les `type alias`.

Commençons par les type alias. Ce sont un peu le plus simple niveau dans lequel on peut exprimer une _forme_ à donner
a une structure sans vraiment lui donner un type. Ils n'existent pas pour vrai (à l'exécution, particulièrement) et ne
sont utilisés que par le compilateur. 

Formellement, les interfaces ressemblent beaucoup à celles de Java. La seule difference majeure, à mon
avis, c'est que les interfaces n'existent qu'au moment de la compilation : elles ne sont pas traduites en Javascript
et ne servent qu'au type checking du compilateur. Elles peuvent aussi être étendues de manière assez particulière
dans un processus que l'on nomme `declaration merging`. C'est un peu une patente utile, mais pas utilisée tous les
jours.

Finalement, les classes. Elles aussi ressemblent beaucoup à celles de Java. Les champs, les méthodes, tout se comporte
de manière semblable. Aussi, les classes existent à l'exécution et ainsi peuvent être identifiées.

Il est important de rappeler que ce qui compte principalement pour Typescript, c'est que la forme des objets soit
compatible. Qu'elle provienne de l'implémentation formelle d'une interface ou bien de coincidence, cela ne change
rien : le compilateur l'acceptera sans problème. On voulait une classe et on passe un objet générique rapidement
crée pour, supposons, un test ? Pas de problème, tant que les méthodes et champs nécéssaires s'y trouvent.

Personnellement, j'utilise les classes et interfaces de manière assez Java. C'est comme ca que je fais depuis
longtemps et je trouve que ca va assez bien. J'utilise les type alias pour deux choses : passer des objets-paramètres 
et décrire des structures de données. Ça me donne la vérification de type que j'aime et ca me donne la flexibilité 
pour définir des objets quand ils sont essentiellement des messages. Ce ne sont peut-être que des idées novices, 
mais vu mes outils, ça semble raisonnable.  

Next post, on commencera.


