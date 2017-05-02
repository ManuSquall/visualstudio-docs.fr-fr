---
title: "Math.acos, fonction (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "acos"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "acos (méthode)"
  - "arcosine (méthode)"
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math.acos, fonction (JavaScript)
Retourne le cosinus d'arc \(ou cosinus inverse\) d'un nombre.  
  
## Syntaxe  
  
```  
Math.acos(number)  
```  
  
#### Paramètres  
 L'argument `number` requis est une expression numérique.  
  
## Valeur de retour  
 Cosinus d'arc de l'argument `number`, en radians.  
  
## Exemple  
 Le code suivant montre comment utiliser la fonction `acos`.  
  
```javascript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## Notes  
 **S'applique à** : [Objet Math](../../javascript/reference/math-object-javascript.md)  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [Math.asin, fonction](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan, fonction](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos, fonction](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin, fonction](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan, fonction](../../javascript/reference/math-tan-function-javascript.md)   
 [Objet Math](../../javascript/reference/math-object-javascript.md)