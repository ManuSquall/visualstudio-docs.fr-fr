---
title: "codePointAt, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# codePointAt, m&#233;thode (String) (JavaScript)
Retourne le point de code d'un caractère Unicode UTF\-16.  
  
## Syntaxe  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### Paramètres  
 `stringObj`  
 Obligatoire.  Objet string.  
  
 `pos`  
 Obligatoire.  Position du caractère.  
  
## Notes  
 Cette méthode retourne les valeurs de point de code, y compris les points de code astral \(points de code avec plus de quatre valeurs hexadécimales\), pour tous les caractères UTF\-16.  
  
 Si `pos` est inférieur à zéro \(0\) ou supérieur à la taille de la chaîne, la valeur de retour est `undefined`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `codePointAt`.  
  
```javascript  
var cp1 = "𠮷".codePointAt(0);  
vary cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]