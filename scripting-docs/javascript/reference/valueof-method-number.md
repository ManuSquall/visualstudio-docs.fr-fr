---
title: "valueOf, m&#233;thode (Number) | Microsoft Docs"
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
ms.assetid: 0242a9ce-d41a-4c9b-af59-e8df32bbd913
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf, m&#233;thode (Number)
Retourne la valeur primitive du nombre spécifié.  
  
## Syntaxe  
  
```  
  
number.valueOf()  
```  
  
#### Paramètres  
 Cette méthode n'a aucun paramètre.  
  
## Valeur de retour  
 Retourne le nombre.  
  
## Notes  
 Dans l'exemple suivant, l'objet Number instancié est identique à la valeur de retour de cette méthode.  
  
```javascript  
var num = 1234;  
var s = num.valueOf();  
  
if (num === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]