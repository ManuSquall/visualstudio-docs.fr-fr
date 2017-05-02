---
title: "has, m&#233;thode (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has, m&#233;thode (Map) (JavaScript)
Retourne `true` si le mappage contient l'élément spécifié.  
  
## Syntaxe  
  
```javascript  
mapObj.has(key)  
```  
  
#### Paramètres  
 `mapObj`  
 Requis.  Objet `Map`.  
  
 `key`  
 Requis.  Clé de l'élément à tester.  
  
## Valeur de propriété\/valeur de retour  
 `true` si le mappage contient l'élément spécifié.  
  
## Exemple  
 L'exemple suivant montre comment ajouter un membre à `Map`, puis vérifier si le mappage le contient.  
  
```javascript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]