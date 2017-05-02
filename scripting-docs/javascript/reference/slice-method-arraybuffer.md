---
title: "slice, m&#233;thode (ArrayBuffer) | Microsoft Docs"
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# slice, m&#233;thode (ArrayBuffer)
Retourne une section d'un [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## Syntaxe  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## Paramètres  
 `arrayBufferObj`  
 Requis.  Objet [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) à partir duquel la section sera copiée.  
  
 `start`  
 Requis.  Index d'octet du début de la section à copier.  
  
 `end`  
 Facultatif.  Index d'octet de la fin de la section à copier.  
  
## Notes  
 La méthode `slice` retourne un objet [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) qui contient la portion indiquée de `arrayBufferObj`.  
  
 La méthode `slice` copie jusqu'à \(sans l'inclure\) l'octet indiqué par `end`.  Si `start` ou `end` est négatif, l'index spécifié est traité comme `length` \+ `start` ou `end`, respectivement, où `length` est la longueur de [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  Si `end` est omis, l'extraction continue jusqu'à la fin de `arrayBufferObj`.  Si `end` se produit avant `start`, aucun octet n'est copié dans le nouveau [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## Exemple  
 Les exemples suivants montrent comment utiliser la méthode `slice`.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Voir aussi  
 [ArrayBuffer, objet](../../javascript/reference/arraybuffer-object.md)