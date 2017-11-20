---
title: "Length, propriété (Uint8ClampedArray) | Documents Microsoft"
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
ms.assetid: de8065a7-04a5-43fa-b5d8-fb2f6c065bfc
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33c22c6e67830239887f41bb12f6aac6ea4afd18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-uint8clampedarray"></a>length, propriété (Uint8ClampedArray)
Longueur du tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
var arrayLength = uint8ClampedArray.length;  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment obtenir la longueur du tableau.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            alert(intArr.length);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)