---
title: Buffer, propriété (Int8Array) | Documents Microsoft
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
ms.assetid: 888ba158-b39e-4260-8ce7-2c370df9c934
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de352e543cb132385a10afa5a4b888c30e11cc64
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633859"
---
# <a name="buffer-property-int8array"></a>buffer, propriété (Int8Array)
Lecture seule. Obtient l'objet ArrayBuffer référencé par ce tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
var arrayBuffer = int8Array.buffer;  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment obtenir le ArrayBuffer du tableau.  
  
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
            alert(intArr.buffer.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]