---
title: "shift, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "shift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "shift (méthode)"
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# shift, m&#233;thode (Array) (JavaScript)
Supprime le premier élément d'un tableau et le retourne.  
  
## Syntaxe  
  
```  
  
arrayObj.shift( )  
```  
  
#### Paramètres  
 La référence `arrayObj` requise est un objet `Array`.  
  
## Valeur de retour  
 Retourne l'élément supprimé du tableau.  
  
## Notes  
 L'exemple suivant illustre l'utilisation de la méthode `shift`.  
  
```javascript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [unshift, méthode \(Array\)](../../javascript/reference/unshift-method-array-javascript.md)