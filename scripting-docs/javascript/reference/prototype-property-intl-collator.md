---
title: "prototype, propri&#233;t&#233; (Intl.Collator) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c1bbb523-fb55-4395-b357-34d91cf5bba0
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype, propri&#233;t&#233; (Intl.Collator)
Retourne une référence au prototype d'un assembleur.  
  
## Syntaxe  
  
```javascript  
collator.prototype  
```  
  
## Notes  
 L'argument `collator` est le nom d'un assembleur.  
  
 Utilisez la propriété `prototype` pour fournir un jeu de fonctionnalités de base à une classe d'objets.  Les nouvelles instances d'un objet « héritent » du comportement du prototype assigné à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Intl.Collator` qui retourne la valeur du plus grand élément de l'ensemble, déclarez la fonction, ajoutez\-la à `Intl.Collator.prototype`, puis utilisez\-la.  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]