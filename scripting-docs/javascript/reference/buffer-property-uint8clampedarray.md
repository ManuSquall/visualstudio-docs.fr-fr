---
title: "buffer, propri&#233;t&#233; (Uint8ClampedArray) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4b87d767-4246-4cf4-bb1d-241b3516397a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# buffer, propri&#233;t&#233; (Uint8ClampedArray)
Lecture seule.  Obtient l'objet [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) référencé par ce tableau.  
  
## Syntaxe  
  
```javascript  
var arrayBuffer = uint8ClampedArray.buffer;  
```  
  
## Exemple  
 L'exemple suivant montre comment obtenir le ArrayBuffer du tableau.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            alert(intArr.buffer.byteLength);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Voir aussi  
 [ArrayBuffer, objet](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray, objet](../../javascript/reference/uint8clampedarray-object-javascript.md)