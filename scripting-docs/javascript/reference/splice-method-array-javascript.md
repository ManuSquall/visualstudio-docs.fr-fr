---
title: "splice, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "splice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "splice (méthode)"
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# splice, m&#233;thode (Array) (JavaScript)
Supprime les éléments d'un tableau et, si nécessaire, insère de nouveaux éléments à leur place, tout en retournant les éléments supprimés.  
  
## Syntaxe  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## Paramètres  
 `arrayObj`  
 Obligatoire.  Objet `Array`.  
  
 `start`  
 Obligatoire.  Dans le tableau, emplacement de base zéro à partir duquel la suppression des éléments commence.  
  
 `deleteCount`  
 Obligatoire.  Nombre d'éléments à supprimer.  
  
 `item1, item2,. . ., itemN`  
 Facultatif.  Éléments à insérer dans le tableau à la place des éléments supprimés.  
  
## Notes  
 La méthode `splice` modifie `arrayObj` en supprimant le nombre d'éléments spécifié à partir de la position `start` et en insérant de nouveaux éléments.  Les éléments supprimés sont retournés sous la forme d'un nouvel objet `Array`.  
  
## Exemple  
 Le code suivant illustre l'utilisation de la méthode `splice`.  
  
```javascript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [Méthode slice \(tableau\)](../../javascript/reference/slice-method-array-javascript.md)