---
title: Math.Round, fonction (JavaScript) | Documents Microsoft
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
- round
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Round method
- Math object
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9543d529e3d0e4e45cff29f1286edbfad8dc0e27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="mathround-function-javascript"></a>Math.round, fonction (JavaScript)
Retourne une expression numérique spécifiée arrondie à l’entier le plus proche.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Math.round(  
number  
)   
```  
  
## <a name="remarks"></a>Remarques  
 Requis `number` argument est la valeur à arrondir à l’entier le plus proche.  
  
 Pour les nombres positifs, si la partie décimale de `number` est 0,5 ou supérieur, la valeur de retour est égale au plus petit entier supérieur à `number`. Si la partie décimale est inférieure à 0,5, la valeur de retour est le plus grand entier inférieur ou égal à `number`.  
  
 Pour les nombres négatifs, si la partie décimale est exactement -0,5, la valeur de retour est le plus petit entier qui est supérieur au nombre.  
  
 Par exemple, `Math.round(8.5)` retourne 9, mais `Math.round(-8.5)` retourne -8.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [Math (objet)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction Math.random](../../javascript/reference/math-random-function-javascript.md)