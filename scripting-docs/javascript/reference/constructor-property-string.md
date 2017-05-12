---
title: "constructor, propri&#233;t&#233; (String) | Microsoft Docs"
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
ms.assetid: ef0e9c82-4651-4404-87b1-d00cad38c6f9
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor, propri&#233;t&#233; (String)
Spécifie la fonction qui crée une chaîne.  
  
## Syntaxe  
  
```  
  
string.constructor  
```  
  
## Notes  
 Le `string` requis est le nom d'une chaîne.  
  
 La propriété `constructor` est un membre du prototype de chaque objet qui en possède un.  Cela inclut tous les objets [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinsèques à l'exception des objets `Global` et `Math`.  La propriété `constructor` contient une référence à la fonction qui crée les instances d'un objet donné.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la propriété constructor.  
  
```javascript  
var x = new String();  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
else  
    document.write("Object is not a String.");  
  
// Output:  
// Object is a String.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]