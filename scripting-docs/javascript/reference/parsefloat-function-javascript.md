---
title: parseFloat, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- parseFloat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parseFloat method
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb8f6d179abba887542e59d083141534732ed42a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="parsefloat-function-javascript"></a>parseFloat, fonction (JavaScript)
Convertit une chaîne en nombre à virgule flottante.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
parseFloat(numString)   
```  
  
## <a name="remarks"></a>Remarques  
 Requis `numString` argument est une chaîne qui contient un nombre à virgule flottante.  
  
 Le `parseFloat` fonction retourne une valeur numérique égale au nombre contenu dans `numString`. Si aucun préfixe de `numString` peut être analysée en un nombre à virgule flottante, `NaN` (pas un nombre) est retourné.  
  
```JavaScript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 Vous pouvez tester `NaN` à l’aide de la `isNaN` (fonction).  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [objet Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [isNaN, fonction](../../javascript/reference/isnan-function-javascript.md)   
 [Fonction parseInt](../../javascript/reference/parseint-function-javascript.md)   
 [Objet String](../../javascript/reference/string-object-javascript.md)