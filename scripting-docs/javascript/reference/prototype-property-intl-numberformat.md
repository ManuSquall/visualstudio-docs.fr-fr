---
title: "prototype, propri&#233;t&#233; (Intl.NumberFormat) | Microsoft Docs"
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
ms.assetid: 7f6a7e26-108b-4b32-97c2-7f96b9252c50
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype, propri&#233;t&#233; (Intl.NumberFormat)
Retourne une référence au prototype d'un formateur.  
  
## Syntaxe  
  
```javascript  
numberFormat.prototype  
```  
  
## Notes  
 L'argument `numberFormat` est le nom d'un formateur.  
  
 Utilisez la propriété `prototype` pour fournir un jeu de fonctionnalités de base à une classe d'objets.  Les nouvelles instances d'un objet « héritent » du comportement du prototype assigné à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Intl.NumberFormat` qui retourne la valeur du plus grand élément de l'ensemble, déclarez la fonction, ajoutez\-la à `Intl.NumberFormat.prototype`, puis utilisez\-la.  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]