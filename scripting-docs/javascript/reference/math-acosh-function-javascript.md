---
title: "Math.acosh, fonction (JavaScript) | Microsoft Docs"
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
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Math.acosh, fonction (JavaScript)
Retourne l'arc cosinus hyperbolique \(ou cosinus hyperbolique inverse\) d'un nombre.  
  
## Syntaxe  
  
```  
Math.acosh(number)  
```  
  
#### Paramètres  
 L'argument `number` requis est une expression numérique.  
  
## Valeur de retour  
 Cosinus hyperbolique inverse de l'argument `number`, en radians.  
  
## Exemple  
 Le code suivant montre comment utiliser la fonction `acosh`.  
  
```javascript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## Notes  
 **S'applique à** : [Objet Math](../../javascript/reference/math-object-javascript.md)  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Voir aussi  
 [Fonction Math.acos](../../javascript/reference/math-acos-function-javascript.md)   
 [Math.asin, fonction](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan, fonction](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos, fonction](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin, fonction](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan, fonction](../../javascript/reference/math-tan-function-javascript.md)   
 [Objet Math](../../javascript/reference/math-object-javascript.md)