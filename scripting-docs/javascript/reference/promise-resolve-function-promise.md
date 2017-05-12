---
title: "Promise.resolve, fonction (Promise) | Microsoft Docs"
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Promise.resolve, fonction (Promise)
Crée une promesse résolue avec un résultat égal à son argument.  
  
## Syntaxe  
  
```  
Promise.resolve(x)  
```  
  
#### Paramètres  
 `x`  
 Obligatoire.  Valeur retournée avec la promesse réalisée.  
  
## Notes  
 La fonction de gestion des réalisations de la méthode `then` s'exécute quand l'objet de promesse réalisée est retourné.  
  
## Exemple  
  
```javascript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Voir aussi  
 [Promise, objet](../../javascript/reference/promise-object-javascript.md)