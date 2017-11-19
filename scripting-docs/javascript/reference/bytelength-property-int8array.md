---
title: "ByteLength, propriété (Int8Array) | Documents Microsoft"
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
ms.assetid: 4e8457a8-2200-4d61-800e-f49fc1e916e5
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c50f49aa7fd9665214fe4269d36766c38891f309
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="bytelength-property-int8array"></a>byteLength, propriété (Int8Array)
Lecture seule. Longueur en octets de ce tableau à partir du début de son ArrayBuffer, telle qu'elle est résolue au moment de la construction.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
var arrayByteLength = int8Array.byteLength;  
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
            var intArr = new Int8Array(buffer.byteLength);  
            alert(intArr.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]