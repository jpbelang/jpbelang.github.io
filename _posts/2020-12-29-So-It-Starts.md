---
layout: post
title: On commence.
---

Merde. Je suis trop occupé (travail, passe-temps). Ça va mieux aller. On avance comme on peut :-).

J'ai quand même eu le temps d'écrire du code un peu. J'expérimente avec mes frameworks.

Avec mon premier framework _typeorm_, je n'ai pas fait grand chose: j'ai écrit la base des relations entre 
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

Mon objet usager est simple : On crée un nouvel usager avec une methode statique `newUser`, qui prend en entrée ses propriétés et 
un mot de passe. 

J'ai fait un test unitaire pour sa création. Il se trouve dans `entities/user.unitspec.ts`, sous le répertoire de tests. 
Y'en a juste un et il n'est pas complet. Encore une fois, j'expérimentais avec `bcrypt`. Aussi, notez que mes tests unitaires 
sont dans des fichiers nommés `unitspec`: c'est pour les différencier des autre genres de tests (d'intégration, par exemple).
Ça nous permet d'avoir des tests qui roulent avec `--watchAll` qui roulent tres vite qui l'on pourrait filtrer basé sur le nom du fichier.

Le seul fichier qui contient un peu de logique est le fichier `entities/user.ts`. 
J'ai deux elements de logique : la creation d'un nouvel usager (`newUser(args: UserData & {password: string})`) et la 
mise à jour d'un mot de passe. J'ai donc écrit un test unitaire pour verifier assez simplement. Ah, là y'en a qui diront: 
"Tu fais pas du TDD?". Oui. Mais ici, je suis plus en mode expérimentation et je ne sais pas du tout où je m'en vais. Aussi, 
le code est _très_ simple.  

Toutes mes autres entités seront formatées de manière semblables. Il serait possible que je change d'idée. J'essaye encore 
de m'assurer de ma bonne compréhension.

Présentement, on n'a pas de DAOs explicites: _typeorm_ crée des _Repository_ (essentiellement des DAOs). Dans mon code, à 
ce moment, ils sont crées du moment de la creation des composantes _express_. Probablement pas une idée brillante (certainement pas,
en fait), mais on va rectifier le tir au fur et à mesure.

Prochain
Onwards and upwards, comme ils disent...