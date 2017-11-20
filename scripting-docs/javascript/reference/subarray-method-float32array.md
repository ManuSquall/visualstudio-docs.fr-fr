---
title: "subarray, méthode (Float32Array) | Documents Microsoft"
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
ms.assetid: 97aa27c0-d650-411e-b929-dd9c4a2ae9a5
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78d8c729298fe80d841d7c4750e4e6817120c9d3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-float32array"></a>subarray, méthode (Float32Array)
Obtient une nouvelle vue Float32Array de la [objet ArrayBuffer](../../javascript/reference/arraybuffer-object.md) pour ce tableau, en spécifiant le premier et le dernier membre du sous-tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
var newFloat32Array = float32Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Paramètres  
 `newFloat32Array`  
 Sous-tableau retourné par cette méthode.  
  
 `begin`  
 Index du début du tableau.  
  
 `end`  
 Index de la fin du tableau.  
  
## <a name="remarks"></a>Remarques  
 Si le paramètre `begin` ou `end` est négatif, il fait référence à un index depuis la fin du tableau, par opposition à depuis le début. Si le paramètre `end` n'est pas spécifié, le sous-tableau contient tous les éléments depuis `begin` à la fin du tableau typé. La plage spécifiée par les valeurs `begin` et `end` est ancrée à la plage d'index valide du tableau en cours. Si la longueur calculée du nouveau tableau typé est négative, elle est ancrée à zéro. Le tableau retourné est du même type que le tableau sur lequel cette méthode est appelée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment obtenir un sous-tableau comportant trois éléments, en commençant par le premier élément du tableau.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var floatArr = new Float32Array(buffer.byteLength / 4);  
            var subArr = floatArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]