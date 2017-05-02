---
title: "values, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: b20699d6-f8b1-4744-8551-9e81c82850dd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# values, m&#233;thode (Array) (JavaScript)
Retourne un itérateur qui retourne les valeurs du tableau.  
  
## Syntaxe  
  
```  
arrayObj.values();  
```  
  
#### Paramètres  
 `arrayObj`  
 Obligatoire.  Objet Array.  
  
## Notes  
  
## Exemple  
 L'exemple suivant montre comment obtenir les valeurs d'un tableau.  
  
```javascript  
var v = ["a", "b", "c"].values();  
// v.next().value == "a"  
// v.next().value == "b"  
// v.next().value == "c"   
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]