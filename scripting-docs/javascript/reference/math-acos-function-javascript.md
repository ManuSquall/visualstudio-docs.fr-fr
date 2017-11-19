---
title: Math.ACOS, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: acos
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- acos method
- arcosine method
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 773499287e215fbc161f289954811d3ef62bcba6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="mathacos-function-javascript"></a>Math.acos, fonction (JavaScript)
Retourne l’arc cosinus (ou cosinus inverse) d’un nombre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Math.acos(number)  
```  
  
#### <a name="parameters"></a>Paramètres  
 L'argument `number` requis est une expression numérique.  
  
## <a name="return-value"></a>Valeur de retour  
 L’arc cosinus de le `number` argument, en radians.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser la fonction `acos`.  
  
```JavaScript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## <a name="remarks"></a>Remarques  
 **S’applique aux**: [Math (objet)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction Math.ASIN](../../javascript/reference/math-asin-function-javascript.md)   
 [Fonction Math.ATAN](../../javascript/reference/math-atan-function-javascript.md)   
 [Fonction Math.Cos](../../javascript/reference/math-cos-function-javascript.md)   
 [Fonction Math.sin](../../javascript/reference/math-sin-function-javascript.md)   
 [Fonction Math.Tan](../../javascript/reference/math-tan-function-javascript.md)   
 [Objet Math](../../javascript/reference/math-object-javascript.md)