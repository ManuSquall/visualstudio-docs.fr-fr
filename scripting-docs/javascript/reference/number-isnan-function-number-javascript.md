---
title: Number.IsNaN, fonction (Number) (JavaScript) | Documents Microsoft
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
ms.assetid: 2d9813d6-ec9c-433b-b060-8e3c3ff62ca4
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c11abe2dd2fc70431800d31f4c44279a88cd75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="numberisnan-function-number-javascript"></a>Number.isNaN, fonction (Number) (JavaScript)
Retourne une valeur booléenne qui indique si une valeur est la valeur réservée `NaN` (pas un nombre).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Number.isNaN(numValue)   
```  
  
#### <a name="parameters"></a>Paramètres  
 `numValue`  
 Obligatoire. Valeur à tester par rapport à `NaN`.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` si la valeur convertie en type `Number` est la valeur `NaN`, sinon `false`.  
  
## <a name="remarks"></a>Remarques  
 Vous utilisez généralement cette méthode pour tester les valeurs de retour des méthodes `parseInt` et `parseFloat`.  
  
 `Number.isNaN` corrige les problèmes avec la fonction `isNaN` globale. `Number.isNaN` convertit uniquement son argument en type Number après l'avoir comparé à `NaN`. Par conséquent, elle retourne `true` si et seulement si l'argument passé a exactement la même valeur que `NaN`. La fonction `isNaN` globale convertit son argument en type Number avant la comparaison, ce qui peut aboutir à des valeurs autres que des nombres qui retournent `true`, alors qu'elles peuvent ne pas retourner `true` pour `Number.isNaN`.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **S’applique aux**: [numéro d’objet](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
// Returns true.  
Number.isNaN(NaN);  
Number.isNaN(Number.NaN);  
Number.isNaN(0 / 0);  
  
// Returns false.  
Number.isNaN(100);  
// Returns false.  
// Strings are converted to numbers and return false.  
Number.isNaN("100");  
Number.isNaN("ABC");  
Number.isNaN("10C");  
Number.isNaN("abc123");  
  
```