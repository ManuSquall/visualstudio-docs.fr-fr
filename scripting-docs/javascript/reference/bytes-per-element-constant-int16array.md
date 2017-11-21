---
title: Bytes_per_element, constante (Int16Array) | Documents Microsoft
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
ms.assetid: b1359cc3-a456-493f-be34-f797dab8ede4
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cd99d1ecaf21061d6a22f68de8d668e7b995825
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="bytesperelement-constant-int16array"></a>BYTES_PER_ELEMENT, constante (Int16Array)
Taille en octets de chaque élément contenu dans le tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
var arraySize = int8Array.BYTES_PER_ELEMENT;  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment obtenir la taille des éléments de tableau.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int16Array(buffer.byteLength / 2);  
            alert(intArr.BYTES_PER_ELEMENT);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]