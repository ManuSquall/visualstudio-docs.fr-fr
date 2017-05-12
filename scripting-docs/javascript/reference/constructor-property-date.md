---
title: "constructor, propri&#233;t&#233; (Date) | Microsoft Docs"
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
ms.assetid: 5db153a1-788b-4a61-bfc8-2d2ec38f36ea
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor, propri&#233;t&#233; (Date)
Spécifie la fonction qui crée une date.  
  
## Syntaxe  
  
```  
  
date.constructor  
```  
  
## Notes  
 Le paramètre `date` requis est le nom d'un objet de date.  
  
 La propriété `constructor` est un membre du prototype de chaque objet qui en possède un.  La propriété `constructor` contient une référence à la fonction qui crée les instances d'un objet donné.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la propriété constructor.  
  
```javascript  
var x = new Date("Hi");  
  
if (x.constructor == Date)  
    document.write("Object is a date.");  
  
// Output:  
// Object is a date.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]