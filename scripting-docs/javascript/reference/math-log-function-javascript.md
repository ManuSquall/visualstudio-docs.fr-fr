---
title: Math.log, fonction (JavaScript) | Documents Microsoft
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
- log
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- log method
- Math object
ms.assetid: 5d617fb5-4b27-404e-842f-eea5549a7c1a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62bfb6bf9bb95b541a51224af4484ded22ccb4e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="mathlog-function-javascript"></a>Math.log, fonction (JavaScript)
Retourne le logarithme naturel (base `e`) d’un nombre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Math.log(number)   
```  
  
#### <a name="parameters"></a>Paramètres  
 nombre  
 Nombre.  
  
## <a name="return-value"></a>Valeur de retour  
 Si `number` est un nombre positif, cette fonction renvoie le logarithme népérien du nombre. Si `number` est négatif, cette fonction retourne `NaN`. Si `number` est 0, cette fonction retourne `-Infinity`.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser cette fonction.  
  
```JavaScript  
var numArr = [ 45.3, 69.0, 557.04, 0.222 ];  
  
for (i in numArr) {  
    document.write(Math.log(numArr[i]));  
    document.write("<br/>");  
}  
  
// Output:   
// 3.8133070324889884  
// 4.23410650459726  
// 6.322637050634291  
// -1.5050778971098575  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [Math (objet)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction Math.sqrt](../../javascript/reference/math-sqrt-function-javascript.md)