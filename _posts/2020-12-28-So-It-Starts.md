---
layout: post
title: Les entités.
---

Merde. Je suis trop occupé (travail, passe-temps). Ça va mieux aller. On avance comme on peut :-).

J'ai quand même eu le temps d'écrire du code un peu. J'expérimente avec mes frameworks.

Avec mon premier framework _typeorm_, je n'ai pas fait grand-chose : j'ai écrit la base des relations entre 
men entités. C'est pas encore vraiment du code. Ce ne sont que des entités de données, sans logique. Il en aura plus tard, 
mais je n'y ai mis que les propriétés. 

Remarquez que j'ai résolu de mettre mes propriétés dans des _types_ TypeScript et pas des interfaces. Les interfaces, dans ma tête, 
c'est pour des actions. Que voulez-vous, je suis vieux. Donc, ce sont mes propriétés pour les `Users`. J'y ai pas mis le mot de passe
parce que je crois que c'est pas là qu'il va finir. J'imagine facilement un objet d'authentication. On verra.

```typescript
export type UserData = {
    name: string,
    email: string,
    gender: Gender
}
```

Je le déclare ensuite comme implémentation.

Mon objet usager est simple : On crée un nouvel usager avec une methode statique `newUser`, qui prend en entrée ses propriétés et 
un mot de passe. 

J'ai fait un test unitaire pour sa création. Il se trouve dans `entities/user.unitspec.ts`, sous le répertoire de tests. 
Il n'y en a qu'un et il n'est pas complet. Encore une fois, j'expérimentais avec `bcrypt`. Aussi, notez que mes tests unitaires 
sont dans des fichiers nommés `unitspec`: c'est pour les différencier des autre genres de tests (d'intégration, par exemple).
Ça nous permet d'avoir des tests qui roulent avec `--watchAll` qui roulent tres vite qui l'on pourrait filtrer basé sur le nom du fichier.

Toutes mes autres entités seront formatées de manière semblables. Il serait possible que je change d'idée. J'essaye encore 
de m'assurer de ma bonne compréhension.

Tout cela dit, `typeorm` semble assez facile d'usage. En fait, ça ressemble beaucoup à `Hibernate` : une annotation déclare l'entité
en tant que telle, et on déclare les relations entre les entités and ces classes de collection (spécifiquement des tableaux dans notre cas).
La seule difficulté (plutôt surprise) que j'ai eu, c'est la nature un peu circulaire des relations :  par exemple, entre `Course` et `FieldOfExpertise`,
on a une collection qui est annotée pour référer à son partenaire. Donc ici, j'ai utilisé des chaînes de caractères plutôt que le nom du type parce que j'avais 
des erreurs au lancement. C'était causé par des problèmes d'initialisation des types dans le système d'annotation de TypeScript. Je crois que 
j'aurais pû utiliser une fonction plutôt qu'une chaine. J'essayerai plus tard...

La seule classe commune que j'ai utilisé (`SimpleVersionedObject`) sert a m'éviter de configurer mon UUID comme clé primaire et 
ma propriété de versionemment.

Finalement, on n'a pas de DAOs explicites : `typeorm` crée des _Repository_ (essentiellement des DAOs). Dans mon code, à 
ce moment, ils sont créés du moment de la creation des composantes `express`. Probablement pas une idée brillante (certainement pas,
en fait), mais on va rectifier le tir au fur et à mesure.

Prochain
Onwards and upwards, comme ils disent...