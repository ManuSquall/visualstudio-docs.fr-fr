---
title: "constructor, propri&#233;t&#233; (Array) | Microsoft Docs"
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
ms.assetid: b78d517b-cb56-4866-b30f-ef8121a27843
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor, propri&#233;t&#233; (Array)
Spécifie la fonction qui crée un tableau.  
  
## Syntaxe  
  
```  
  
array.constructor  
```  
  
## Notes  
 Le `array` requis est le nom d'un tableau.  
  
 La propriété `constructor` est un membre du prototype de chaque objet qui en possède un.  Cela inclut tous les objets [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinsèques à l'exception des objets `Global` et `Math`.  La propriété `constructor` contient une référence à la fonction qui crée les instances d'un objet donné.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la propriété constructor.  
  
```javascript  
var x = new Array();  
  
if (x.constructor == Array)  
    document.write("Object is an Array.");  
else  
    document.write("Object is not an Array.");  
  
// Output:  
// Object is an Array.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]