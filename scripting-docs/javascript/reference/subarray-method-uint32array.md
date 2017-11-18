---
title: "subarray, méthode (Uint32Array) | Documents Microsoft"
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
ms.assetid: 4c183208-12ec-4051-bf0f-a4f7c112cea1
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1c76c5c83bcb1e43b51b4f49618e72311d5df86
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-uint32array"></a>subarray, méthode (Uint32Array)
Obtient une nouvelle vue Uint32Array de la [objet ArrayBuffer](../../javascript/reference/arraybuffer-object.md) pour ce tableau, en spécifiant le premier et le dernier membre du sous-tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
var newUint32Array = uint32Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Paramètres  
 `newUint32Array`  
 Sous-tableau retourné par cette méthode.  
  
 `begin`  
 Index du début du tableau.  
  
 `end`  
 Index de la fin du tableau. Il est non inclusif.  
  
## <a name="remarks"></a>Remarques  
 Si le paramètre `begin` ou `end` est négatif, il fait référence à un index depuis la fin du tableau, par opposition à depuis le début. Si le paramètre `end` n'est pas spécifié, le sous-tableau contient tous les éléments depuis `begin` à la fin du tableau typé. La plage spécifiée par les valeurs `begin` et `end` est ancrée à la plage d'index valide du tableau en cours. Si la longueur calculée du nouveau tableau typé est négative, elle est ancrée à zéro. Le tableau retourné est du même type que le tableau sur lequel cette méthode est appelée.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment obtenir un sous-tableau comportant deux éléments, en commençant par le premier élément du tableau.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]