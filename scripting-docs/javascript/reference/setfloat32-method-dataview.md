---
title: "setFloat32, m&#233;thode (DataView) | Microsoft Docs"
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
ms.assetid: b3f68048-c817-48d2-bc17-945e3bcc94d7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setFloat32, m&#233;thode (DataView)
Définit la valeur Float32 sur l'offset d'octets spécifié à partir du début de la vue.  Il n'existe aucune contrainte d'alignement ; les valeurs multioctets peuvent être définies sur n'importe quel offset.  
  
## Syntaxe  
  
```  
dataView.setFloat32 (byteOffset, value, littleEndian);   
```  
  
## Paramètres  
 `byteOffset`  
 Emplacement dans la mémoire tampon auquel la valeur doit être récupérée.  
  
 `value`  
 Valeur à définir.  
  
 `littleEndian`  
 Facultatif.  Si la valeur est False ou Undefined, une valeur avec primauté des octets de poids fort \(big\-endian\) doit être écrite, sinon une valeur avec primauté des octets de poids faible \(little\-endian\) doit être écrite.  
  
## Notes  
 Ces méthodes lèvent une exception si elles doivent écrire au\-delà de la fin de la vue.  
  
## Exemple  
 L'exemple suivant montre comment définir le premier Float32 dans le DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setFloat32(0, 9.1);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]