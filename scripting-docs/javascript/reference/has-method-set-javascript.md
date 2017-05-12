---
title: "has, m&#233;thode (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has, m&#233;thode (Set) (JavaScript)
Retourne `true` si l'ensemble contient l'élément spécifié.  
  
## Syntaxe  
  
```javascript  
setObj.has(value)  
```  
  
#### Paramètres  
 `setObj`  
 Requis.  Objet `Set`.  
  
 `value`  
 Requis.  Élément à tester.  
  
## Valeur de propriété\/valeur de retour  
 `true` si l'ensemble contient l'élément spécifié.  
  
## Exemple  
 L'exemple suivant montre comment ajouter des membres à `Set`, puis vérifier si l'ensemble contient un membre spécifique.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]