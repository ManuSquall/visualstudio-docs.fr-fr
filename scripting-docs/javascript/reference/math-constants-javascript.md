---
title: "Math, constantes (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "LN2 (constante) (JavaScript)"
  - "E (constante) (JavaScript)"
  - "LOG10E (constante) (JavaScript)"
  - "SQRT1_2 (constante) (JavaScript)"
  - "LOG2E (constante) (JavaScript)"
  - "Math.SQRT2 (constante) (JavaScript)"
  - "pi (constante) (JavaScript)"
  - "Math.LOG2E (constante) (JavaScript)"
  - "constantes (JavaScript), math"
  - "Math.E (constante) (JavaScript)"
  - "logarithme (constantes) (JavaScript)"
  - "Math.LOG10E (constante) (JavaScript)"
  - "Math.SQRT1_2 (constante) (JavaScript)"
  - "SQRT2 (constante) (JavaScript)"
  - "racine carrée (constante) (JavaScript)"
  - "Math.PI (constante) (JavaScript)"
  - "math (constantes) (JavaScript)"
  - "LN10 (constante) (JavaScript)"
  - "Math.LN2 (constante) (JavaScript)"
  - "Math.LN10 (constante) (JavaScript)"
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math, constantes (JavaScript)
Les constantes Math retournent des valeurs constantes qui sont des propriétés de l'objet `Math`.  
  
## Constantes d'objet Math  
 Le tableau suivant répertorie les valeurs de constante qui sont des propriétés de l'[objet Math](../../javascript/reference/math-object-javascript.md).  
  
|Constante|Description|Valeur approximative|  
|---------------|-----------------|--------------------------|  
|`Math.E`|Constante mathématique e.  Il s'agit du nombre d'Euler, qui constitue la base des logarithmes népériens.|2.718|  
|`Math.LN2`|Logarithme népérien de 2.|0.693|  
|`Math.LN10`|Logarithme népérien de 10.|2.302|  
|`Math.LOG2E`|Logarithme de base 2 de e.|1.443|  
|`Math.LOG10E`|Logarithme de base 10 de e.|0.434|  
|`Math.PI`|Pi.  Il s'agit du rapport entre la circonférence d'un cercle et son diamètre.|3.14159|  
|`Math.SQRT1_2`|Racine carrée de 0,5 ou, de manière équivalente, 1 divisé par la racine carrée de 2.|0.707|  
|`Math.SQRT2`|Racine carrée de 2.|1.414|  
  
## Exemple  
 L'exemple ci\-dessous montre comment utiliser la constante `Math.PI`.  
  
```javascript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Objet Math](../../javascript/reference/math-object-javascript.md)  
  
## Voir aussi  
 [Constantes numériques](../../javascript/reference/number-constants-javascript.md)   
 [JavaScript, constantes](../../javascript/reference/javascript-constants.md)