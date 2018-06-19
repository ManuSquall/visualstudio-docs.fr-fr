---
title: Math.ACOSH, fonction (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd75140dfcf3d9ac703c2aeadf68bea4da9e0dc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639039"
---
# <a name="mathacosh-function-javascript"></a>Math.acosh, fonction (JavaScript)
Retourne l'arc cosinus hyperbolique (ou cosinus hyperbolique inverse) d'un nombre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Math.acosh(number)  
```  
  
#### <a name="parameters"></a>Paramètres  
 L'argument `number` requis est une expression numérique.  
  
## <a name="return-value"></a>Valeur de retour  
 Cosinus hyperbolique inverse de l'argument `number`, en radians.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser la fonction `acosh`.  
  
```JavaScript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## <a name="remarks"></a>Remarques  
 **S’applique aux**: [Math (objet)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction Math.ACOS](../../javascript/reference/math-acos-function-javascript.md)   
 [Fonction Math.ASIN](../../javascript/reference/math-asin-function-javascript.md)   
 [Fonction Math.ATAN](../../javascript/reference/math-atan-function-javascript.md)   
 [Fonction Math.Cos](../../javascript/reference/math-cos-function-javascript.md)   
 [Fonction Math.sin](../../javascript/reference/math-sin-function-javascript.md)   
 [Fonction Math.Tan](../../javascript/reference/math-tan-function-javascript.md)   
 [Objet Math](../../javascript/reference/math-object-javascript.md)