---
title: subarray, méthode (Int8Array) | Documents Microsoft
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
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e32c3a0da7e3173273eb40bf52bb6583bd77df51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640009"
---
# <a name="subarray-method-int8array"></a>subarray, méthode (Int8Array)
Obtient une nouvelle vue Int8Array de la mémoire ArrayBuffer pour ce tableau qui référence les éléments du début (inclus) jusqu'à la fin (exclus).  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## <a name="parameters"></a>Paramètres  
 `newInt8Array`  
 Sous-tableau retourné par cette méthode.  
  
 `begin`  
 Index du début du tableau.  
  
 `end`  
 Index de la fin du tableau. Il est non inclusif.  
  
## <a name="remarks"></a>Remarques  
 Si le paramètre de début ou de fin est négatif, il fait référence à un index de la fin du tableau, par opposition au début. Si le paramètre de fin n'est pas spécifié, le sous-tableau contient tous les éléments du début à la fin du TypedArray. La plage spécifiée par les valeurs de début et de fin est ancrée à la plage d'index valide du tableau en cours. Si la longueur calculée du nouveau TypedArray est négative, elle est ancrée à zéro. Le TypedArray retourné est du même type que le tableau sur lequel cette méthode est appelée.  
  
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
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]