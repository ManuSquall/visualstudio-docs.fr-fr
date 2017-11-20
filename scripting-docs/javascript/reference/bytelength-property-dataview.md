---
title: "ByteLength, propriété (DataView) | Documents Microsoft"
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
ms.assetid: 6274285f-b673-48f6-a1e7-89ff7ee348b5
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2a9eb55a40722c42ccc9711c434061e98b64039
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="bytelength-property-dataview"></a>byteLength, propriété (DataView)
Lecture seule. Longueur en octets de cette vue à partir du début de son ArrayBuffer, telle qu'elle est résolue au moment de la construction.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
var byteLength = dataView.byteLength;  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment obtenir la longueur d'un DataView à partir d'un XMLHttpRequest.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]