---
title: "Promise.reject, fonction (Promise) | Microsoft Docs"
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Promise.reject, fonction (Promise)
Crée une promesse rejetée avec un résultat égal à l'argument transmis.  
  
## Syntaxe  
  
```  
Promise.reject(r);  
```  
  
#### Paramètres  
 `r`  
 Obligatoire.  Motif de rejet de la promesse.  
  
## Notes  
 La fonction de gestion d'erreurs de la méthode `then` ou `catch` s'exécute quand la promesse rejetée est retournée.  
  
## Exemple  
  
```javascript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Voir aussi  
 [Promise, objet](../../javascript/reference/promise-object-javascript.md)