---
title: "keys, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: fc5b6a30-642c-4bd7-ad31-a42667af2f3f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# keys, m&#233;thode (Array) (JavaScript)
Retourne un itérateur qui retourne les valeurs d'index du tableau.  
  
## Syntaxe  
  
```  
arrayObj.keys();  
```  
  
#### Paramètres  
 `arrayObj`  
 Obligatoire.  Objet Array.  
  
## Notes  
  
## Exemple  
 L'exemple suivant montre comment obtenir les valeurs de clés d'un tableau.  
  
```javascript  
var k = ["a", "b", "c"].keys();  
// k.next().value == 0  
// k.next().value == 1  
// k.next().value == 2   
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]