---
title: isNaN, fonction (JavaScript) | Documents Microsoft
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
- isNaN
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- isNaN method
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7e6d3687e795ea5d5e38308a8af0d73ba7f5ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="isnan-function-javascript"></a>isNaN, fonction (JavaScript)
Retourne une valeur booléenne qui indique si une valeur est la valeur réservée `NaN` (pas un nombre).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
isNaN(numValue)   
```  
  
## <a name="return-value"></a>Valeur de retour  
 `true` si la valeur convertie en type `Number` est la valeur `NaN`, sinon `false`.  
  
## <a name="remarks"></a>Remarques  
 Requis `numValue` est la valeur à tester pour `NaN`.  
  
 Vous utilisez généralement cette méthode pour tester les valeurs de retour des méthodes `parseInt` et `parseFloat`.  
  
 Vous pouvez également une variable qui contient `NaN` ou une autre valeur peut être comparée à elle-même. Si elle compare différente, il est `NaN`. C’est parce que `NaN` est la seule valeur qui n’est pas égale à elle-même.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [objet Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## <a name="see-also"></a>Voir aussi  
 [isFinite, fonction](../../javascript/reference/isfinite-function-javascript.md)   
 [NaN, constante](../../javascript/reference/nan-constant-javascript.md)   
 [Fonction parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [Fonction parseInt](../../javascript/reference/parseint-function-javascript.md)