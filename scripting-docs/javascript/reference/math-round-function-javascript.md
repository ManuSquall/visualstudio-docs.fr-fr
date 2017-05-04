---
title: "Math.round, fonction (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "round"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Math (objet)"
  - "Round (méthode)"
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math.round, fonction (JavaScript)
Retourne l'expression numérique spécifiée arrondie à l'entier le plus proche.  
  
## Syntaxe  
  
```  
  
Math.round(  
number  
)   
```  
  
## Notes  
 L'argument `number` requis est la valeur qui va être arrondie à l'entier le plus proche.  
  
 Pour les nombres positifs, si la partie décimale de l'argument `number` est égale ou supérieure à 0,5, la valeur de retour est égale au plus petit entier supérieur à `number`.  Si la partie décimale est inférieure à 0,5, la valeur de retour correspond au plus grand entier inférieur ou égal à `number`.  
  
 Pour les nombres négatifs, si la partie décimale est exactement égale à \-0,5, la valeur de retour est le plus petit entier supérieur au nombre.  
  
 Par exemple, `Math.round(8.5)` retourne 9, mais `Math.round(-8.5)` retourne \-8.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Objet Math](../../javascript/reference/math-object-javascript.md)  
  
## Voir aussi  
 [Math.random, fonction](../../javascript/reference/math-random-function-javascript.md)