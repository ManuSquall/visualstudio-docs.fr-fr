---
title: "prototype, propri&#233;t&#233; (WeakMap) | Microsoft Docs"
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype, propri&#233;t&#233; (WeakMap)
Retourne une référence au prototype d'un objet `WeakMap`.  
  
## Syntaxe  
  
```javascript  
weakmap.prototype  
```  
  
## Notes  
 L'argument `weakmap` est le nom d'un objet `WeakMap`.  
  
 Utilisez la propriété `prototype` pour fournir un jeu de fonctionnalités de base à une classe d'objets.  Les nouvelles instances d'un objet « héritent » du comportement du prototype assigné à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `WeakMap` qui retourne la valeur du plus grand élément du `WeakMap`, déclarez la fonction, ajoutez\-la à `WeakMap.prototype`, puis utilisez\-la.  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]