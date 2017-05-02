---
title: "setUint16, m&#233;thode (DataView) | Microsoft Docs"
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
ms.assetid: bdf47cda-7fa5-4aaa-8aa2-8cf9a8d56cb3
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setUint16, m&#233;thode (DataView)
Définit la valeur Uint16 sur l'offset d'octets spécifié à partir du début de la vue.  Il n'existe aucune contrainte d'alignement ; les valeurs multioctets peuvent être définies sur n'importe quel offset.  
  
## Syntaxe  
  
```  
dataView.setUint16(byteOffset, value, littleEndian);   
```  
  
## Paramètres  
 `testInt`  
 Obligatoire.  Valeur Uint16 retournée par la méthode.  
  
 `value`  
 Valeur à définir.  
  
 `byteOffset`  
 Emplacement dans la mémoire tampon auquel la valeur doit être récupérée.  
  
 `littleEndian`  
 Facultatif.  Si la valeur est False ou Undefined, une valeur avec primauté des octets de poids fort \(big\-endian\) doit être écrite, sinon une valeur avec primauté des octets de poids faible \(little\-endian\) doit être écrite.  
  
## Notes  
 Ces méthodes lèvent une exception si elles doivent écrire au\-delà de la fin de la vue.  
  
## Exemple  
 L'exemple suivant montre comment définir le premier Uint16 dans le DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint16(0, 9);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]