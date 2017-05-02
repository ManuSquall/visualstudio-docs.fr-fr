---
title: "byteOffset, propri&#233;t&#233; (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: bfc22cf4-00e3-4e2c-8419-032b179aa8da
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# byteOffset, propri&#233;t&#233; (Uint8ClampedArray)
Lecture seule.  Décalage en octets de ce tableau à partir du début de son [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), telle qu'il est défini au moment de la construction.  
  
## Syntaxe  
  
```javascript  
var arrayOffset = uint8ClampedArray.byteOffset;  
```  
  
## Exemple  
 L'exemple suivant montre comment obtenir le décalage du tableau.  
  
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
            alert(intArr.byteOffset);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Voir aussi  
 [ArrayBuffer, objet](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray, objet](../../javascript/reference/uint8clampedarray-object-javascript.md)