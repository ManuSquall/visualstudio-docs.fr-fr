---
title: "prototype, propri&#233;t&#233; (Map) | Microsoft Docs"
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
ms.assetid: c7b429cb-97b7-400e-a214-1b18bddd6b02
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype, propri&#233;t&#233; (Map)
Retourne une référence au prototype pour un mappage.  
  
## Syntaxe  
  
```javascript  
map.prototype  
```  
  
## Notes  
 L'argument `map` est le nom d'un mappage.  
  
 Utilisez la propriété `prototype` pour fournir un jeu de fonctionnalités de base à une classe d'objets.  Les nouvelles instances d'un objet « héritent » du comportement du prototype assigné à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Map` qui retourne la valeur du plus grand élément de l'ensemble, déclarez la fonction, ajoutez\-la à `Map.prototype`, puis utilisez\-la.  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]