---
title: "constructor, propri&#233;t&#233; (Set) | Microsoft Docs"
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
ms.assetid: f350b7eb-8994-40bf-9011-f8b20fcef34f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# constructor, propri&#233;t&#233; (Set)
Spécifie la fonction qui crée un ensemble.  
  
## Syntaxe  
  
```javascript  
set.constructor  
```  
  
## Notes  
 Le paramètre obligatoire `set` est le nom de l'ensemble.  
  
 La propriété `constructor` est un membre du prototype de chaque objet qui en possède un.  Cela inclut tous les objets JavaScript intrinsèques, excepté les objets `Global` et `Math`.  La propriété `constructor` contient une référence à la fonction qui crée les instances d'un objet donné.  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]