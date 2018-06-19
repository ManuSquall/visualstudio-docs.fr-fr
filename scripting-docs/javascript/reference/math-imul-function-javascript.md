---
title: Math.imul, fonction (JavaScript) | Documents Microsoft
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
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57820d0926d574c75924f4eef6265ef7fa0766da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638869"
---
# <a name="mathimul-function-javascript"></a>Math.imul, fonction (JavaScript)
Retourne le produit de deux nombres traités comme des entiers signés 32 bits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Math.imul(x, y);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `x`  
 Obligatoire. Premier nombre.  
  
 `y`  
 Obligatoire. Second nombre.  
  
## <a name="remarks"></a>Remarques  
 Cette fonction est utilisée pour les compilateurs comme Emscripten et Mandreel, qui n'implémentent pas la multiplication d'entiers de la même manière que JavaScript.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment multiplier des nombres avec `Math.imul`.  
  
```JavaScript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2   
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]