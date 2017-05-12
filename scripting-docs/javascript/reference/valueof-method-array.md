---
title: "valueOf, m&#233;thode (Array) | Microsoft Docs"
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
ms.assetid: b694fe65-1297-4580-8af2-406932c06454
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf, m&#233;thode (Array)
Retourne la valeur primitive de l'objet spécifié.  
  
## Syntaxe  
  
```  
  
array.valueOf()  
```  
  
#### Paramètres  
 Cette méthode n'a aucun paramètre.  
  
## Valeur de retour  
 Retourne l'instance de tableau.  
  
## Notes  
 Dans l'exemple suivant, l'objet tableau instancié équivaut à la valeur de retour de cette méthode.  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.valueOf();  
  
if (arr === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]