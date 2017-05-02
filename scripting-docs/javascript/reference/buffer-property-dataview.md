---
title: "buffer, propri&#233;t&#233; (DataView) | Microsoft Docs"
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
ms.assetid: b69afc28-586e-4277-8cd6-b9d69a54fb55
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# buffer, propri&#233;t&#233; (DataView)
Lecture seule.  Obtient l'ArrayBuffer référencé par cette vue.  
  
## Syntaxe  
  
```javascript  
var arrayBuffer = dataView.buffer;  
```  
  
## Exemple  
 L'exemple suivant montre la façon dont est obtenue la longueur de l'ArrayBuffer sous\-jacente du DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.buffer.byteLength)  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]