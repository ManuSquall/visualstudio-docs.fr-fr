---
title: Object.is, fonction (JavaScript) | Documents Microsoft
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
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36d4c281fdafbfacb0b1f6061ef4a90bfac99234
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638699"
---
# <a name="objectis-function-javascript"></a>Object.is, fonction (JavaScript)
Retourne une valeur qui indique si deux valeurs sont identiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
Object.is(value1, value2)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `value1`  
 Obligatoire. Première valeur à tester.  
  
 `value2`  
 Obligatoire. Seconde valeur à tester.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` si la valeur est identique ; sinon, `false`.  
  
## <a name="remarks"></a>Remarques  
 Contrairement à l'opérateur ==, `Object.is` ne force aucun type lors du test des valeurs.  
  
 La comparaison appliquée par `Object.is` est similaire à celle appliquée par l'opérateur ===, à ceci près qu'`Object.is` traite `Number.isNaN` comme la même valeur que `NaN`. Il traite également +0 et -0 comme des valeurs différentes.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]