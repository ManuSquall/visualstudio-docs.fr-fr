---
title: Array.of, fonction (Array) (JavaScript) | Documents Microsoft
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
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 042315bbc3b956e92fff866f7d403b6f87726a74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633979"
---
# <a name="arrayof-function-array-javascript"></a>Array.of, fonction (Array) (JavaScript)
Retourne un tableau à partir des arguments transmis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `element0,...,elementN`  
 Facultatif. Éléments à placer dans le tableau. Ce paramètre crée un tableau avec n + 1 éléments et une longueur de n + 1.  
  
## <a name="remarks"></a>Remarques  
 Cette fonction est similaire à l'appel de `new Array(args)`, mais `Array.of` n'inclut pas de comportement spécial quand un argument est passé.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée un tableau à partir des nombres transmis.  
  
```JavaScript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1   
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre la différence entre l'utilisation de `Array.of` et de `new Array`.  
  
```JavaScript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]