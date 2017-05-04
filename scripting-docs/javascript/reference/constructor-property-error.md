---
title: "constructor, propri&#233;t&#233; (Error) | Microsoft Docs"
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
ms.assetid: 18aea278-2bd5-457b-83a5-d8d8f1226e0c
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor, propri&#233;t&#233; (Error)
Spécifie la fonction qui crée une erreur.  
  
## Syntaxe  
  
```  
  
error.constructor  
```  
  
## Notes  
 Le paramètre `error` requis est le nom d'un objet d'erreur.  
  
 La propriété `constructor` est un membre du prototype de chaque objet qui en possède un.  La propriété `constructor` contient une référence à la fonction qui crée les instances d'un objet donné.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la propriété constructor.  
  
```javascript  
var x = new Error("This is an error");  
  
if (x.constructor == Error)  
    document.write("Object is an error.");  
  
// Output:  
// Object is an error.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]