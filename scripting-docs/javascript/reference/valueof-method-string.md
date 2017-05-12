---
title: "valueOf, m&#233;thode (String) | Microsoft Docs"
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
ms.assetid: dfb55e6b-e38f-4b49-8196-9693f87126a4
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf, m&#233;thode (String)
Retourne la chaîne.  
  
## Syntaxe  
  
```  
  
string.valueOf()  
```  
  
#### Paramètres  
 Cette méthode n'a aucun paramètre.  
  
## Valeur de retour  
 Retourne la valeur de chaîne.  
  
## Notes  
 Dans l'exemple suivant, l'objet String est identique à la valeur de retour.  
  
```javascript  
var str = "every good boy does fine";  
var strStr = str.valueOf();  
  
if (str === strStr)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]