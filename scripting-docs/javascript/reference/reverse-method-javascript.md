---
title: "reverse, m&#233;thode (JavaScript) | Microsoft Docs"
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
  - "reverse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "tableaux (Visual Studio), inverser les éléments"
  - "reverse (méthode)"
  - "transposer des éléments"
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# reverse, m&#233;thode (JavaScript)
Inverse les éléments dans un objet `Array`.  
  
## Syntaxe  
  
```  
  
arrayObj.reverse()   
```  
  
## Paramètres  
 `arrayObj`  
 Requis.  Tout objet `Array`.  
  
## Valeur de retour  
 Tableau inversé.  
  
## Notes  
 La référence `arrayObj` requise est un objet `Array`.  
  
 La méthode `reverse` inverse les éléments d'un objet `Array` existant.  Aucun nouvel objet `Array` n'est créé pendant l'exécution.  
  
 Si le tableau n'est pas contigu, la méthode `reverse` crée des éléments dans le tableau pour remplir les espaces vides de ce dernier.  Chacun de ces éléments créés prend la valeur `undefined`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `reverse`.  
  
```javascript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Voir aussi  
 [Méthode concat \(tableau\)](../../javascript/reference/concat-method-array-javascript.md)