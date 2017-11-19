---
title: Math, constantes (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- LN2 constant [JavaScript]
- E constant [JavaScript]
- LOG10E constant [JavaScript]
- SQRT1_2 constant [JavaScript]
- LOG2E constant [JavaScript]
- Math.SQRT2 constant [JavaScript]
- PI constant [JavaScript]
- Math.LOG2E constant [JavaScript]
- constants [JavaScript], math
- Math.E constant [JavaScript]
- logarithm consants [JavaScript]
- Math.LOG10E constant [JavaScript]
- Math.SQRT1_2 constant [JavaScript]
- SQRT2 constant [JavaScript]
- square root constants [JavaScript]
- Math.PI constant [JavaScript]
- math constants [JavaScript]
- LN10 constant [JavaScript]
- Math.LN2 constant [JavaScript]
- Math.LN10 constant [JavaScript]
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9942abb69af416cd4cd7f092dc9f1478e0bc3a69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="math-constants-javascript"></a>Math, constantes (JavaScript)
Constantes mathématiques retournent des valeurs constantes qui sont des propriétés de la `Math` objet.  
  
## <a name="math-object-constants"></a>Constantes d'objet Math  
 Le tableau suivant répertorie les valeurs constantes qui sont des propriétés de la [Math, objet](../../javascript/reference/math-object-javascript.md).  
  
|Constante|Description|Valeur approximative|  
|--------------|-----------------|-----------------------|  
|`Math.E`|Constante mathématique e. Il s'agit du nombre d'Euler, la base du logarithme naturel.|2.718|  
|`Math.LN2`|Logarithme népérien de 2.|0.693|  
|`Math.LN10`|Logarithme népérien de 2.|2.302|  
|`Math.LOG2E`|Logarithme de base 2 de e.|1.443|  
|`Math.LOG10E`|Logarithme de base 10 de e.|0.434|  
|`Math.PI`|Pi. Rapport de la circonférence d'un cercle à son diamètre.|3.14159|  
|`Math.SQRT1_2`|Racine carrée de 0,5, ou, de façon équivalente, un divisé par la racine carrée de 2.|0.707|  
|`Math.SQRT2`|Racine carrée de 2.|1.414|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre comment utiliser le `Math.PI` constante.  
  
```JavaScript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [Math (objet)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes numériques](../../javascript/reference/number-constants-javascript.md)   
 [Constantes JavaScript](../../javascript/reference/javascript-constants.md)