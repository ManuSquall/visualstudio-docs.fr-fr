---
title: "setUint8, m&#233;thode (DataView) | Microsoft Docs"
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
ms.assetid: b294262b-3f4b-4183-a292-5a6982cbdd27
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setUint8, m&#233;thode (DataView)
Stocke une valeur Uint8 au niveau de l'offset d'octet spécifié à partir du début de la vue.  
  
## Syntaxe  
  
```  
dataView.setUint8(byteOffset, value);   
```  
  
## Paramètres  
 `byteOffset`  
 Emplacement dans la mémoire tampon auquel la valeur doit être définie.  
  
 `value`  
 Valeur à définir.  
  
## Notes  
 Ces méthodes lèvent une exception si elles doivent écrire au\-delà de la fin de la vue.  
  
## Exemple  
 L'exemple suivant montre comment définir le premier Uint8 dans le DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint8(0, 9);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]