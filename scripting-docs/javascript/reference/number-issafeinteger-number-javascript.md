---
title: Number.isSafeInteger (nombre) (JavaScript) | Documents Microsoft
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
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eebc2147bc5043341be7e883548af825922036f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="numberissafeinteger-number-javascript"></a>Number.isSafeInteger (Number) (JavaScript)
Retourne une valeur booléenne qui indique si un nombre peut être représenté en toute sécurité en JavaScript.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## <a name="return-value"></a>Valeur de retour  
 `true` si le nombre est compris entre `Number.MIN_SAFE_INTEGER` et `Number.MAX_SAFE_INTEGER` (inclus) ; sinon `false`.  
  
## <a name="remarks"></a>Remarques  
 Un entier sûr en JavaScript est un nombre double précision IEEE-754 avant l'application d'un arrondi.  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **S’applique aux**: [numéro d’objet](../../javascript/reference/number-object-javascript.md)