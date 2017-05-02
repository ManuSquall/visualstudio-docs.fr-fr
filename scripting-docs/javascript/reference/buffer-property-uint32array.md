---
title: "buffer, propri&#233;t&#233; (Uint32Array) | Microsoft Docs"
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
ms.assetid: 7bd098c5-25c4-4e45-aeb2-95cc8f2325dc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# buffer, propri&#233;t&#233; (Uint32Array)
Lecture seule.  Obtient l'ArrayBuffer référencé par ce tableau.  
  
## Syntaxe  
  
```javascript  
var arrayBuffer = uint32Array.buffer;  
```  
  
## Exemple  
 L'exemple suivant montre comment obtenir l'ArrayBuffer du tableau.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            alert(intArr.buffer.byteLength);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]