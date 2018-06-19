---
title: Number.isinteger, fonction (Number) (JavaScript) | Documents Microsoft
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
ms.assetid: 54fcf68c-0067-4bad-af94-d7ff8c88914a
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20e1b7b463003d3a25ef64bba793b3273371266b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638799"
---
# <a name="numberisinteger-function-number-javascript"></a>Number.isInteger, fonction (Number) (JavaScript)
Retourne une valeur booléenne qui indique si une valeur est un entier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Number.isInteger(numValue)   
```  
  
## <a name="return-value"></a>Valeur de retour  
 `true` si la valeur est un entier, sinon `false`.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **S’applique aux**: [numéro d’objet](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
// Returns true  
Number.isInteger(100)  
Number.isInteger(-100)  
  
// Returns false  
Number.isInteger(Number.NaN)  
Number.isInteger(Infinity)  
Number.isInteger(100 / 3)  
Number.isInteger("100")  
  
```