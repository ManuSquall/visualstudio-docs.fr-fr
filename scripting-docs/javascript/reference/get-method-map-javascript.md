---
title: "get, m&#233;thode (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# get, m&#233;thode (Map) (JavaScript)
Retourne un élément spécifique à partir d'un mappage.  
  
## Syntaxe  
  
```javascript  
mapObj.get(key)  
```  
  
#### Paramètres  
 `mapObj`  
 Requis.  Objet `Map`.  
  
 `key`  
 Requis.  Clé d'un élément dans `Map`.  
  
## Valeur de propriété\/valeur de retour  
 Retourne l'objet associé à la clé.  Si `Map` ne contient pas la clé, cette méthode retourne une valeur `undefined`.  
  
## Exemple  
 L'exemple suivant montre comment récupérer un élément dans un objet `Map`.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]