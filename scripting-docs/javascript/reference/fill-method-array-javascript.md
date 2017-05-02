---
title: "fill, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# fill, m&#233;thode (Array) (JavaScript)
Remplit un tableau avec une valeur spécifiée.  
  
## Syntaxe  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### Paramètres  
 `arrayObj`  
 Obligatoire.  Objet Array.  
  
 `value`  
 Obligatoire.  Valeur utilisée pour remplir le tableau.  
  
 `start`  
 Facultatif.  Index de départ utilisé pour remplir les valeurs de tableau.  La valeur par défaut est 0.  
  
 `end`  
 Facultatif.  Index de fin utilisé pour remplir les valeurs de tableau.  La valeur par défaut est la propriété de longueur de l'objet `this`.  
  
## Notes  
 Si `start` est négatif, `start` est considéré comme `length`\+`start`, où `length` est la longueur du tableau.  Si `end` est négatif, `end` est considéré comme `length`\+`end`.  
  
## Exemple  
 Les exemples de code suivants remplissent un tableau avec des valeurs.  
  
```javascript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]