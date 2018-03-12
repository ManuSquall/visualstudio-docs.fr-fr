---
title: "unshift, méthode (Array) (JavaScript) | Documents Microsoft"
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
- unshift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unshift method
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3f0d210514d04afa5cf467819a5e843925e1a68
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="unshift-method-array-javascript"></a>unshift, méthode (Array) (JavaScript)
Insère de nouveaux éléments au début d'un tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## <a name="parameters"></a>Paramètres  
 `arrayObj`  
 Obligatoire. Objet `Array`.  
  
 `item1, item2,. . ., itemN`  
 Facultatif. Éléments à insérer au début de la `Array`.  
  
## <a name="remarks"></a>Remarques  
 Le `unshift` méthode insère les éléments dans le début d’un tableau, pour qu’elles apparaissent dans le même ordre que celui dans lequel elles apparaissent dans la liste d’arguments.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `unshift`.  
  
```JavaScript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode shift (Array)](../../javascript/reference/shift-method-array-javascript.md)