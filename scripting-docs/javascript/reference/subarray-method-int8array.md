---
title: "subarray, m&#233;thode (Int8Array) | Microsoft Docs"
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
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# subarray, m&#233;thode (Int8Array)
Obtient une nouvelle vue Int8Array de la mémoire ArrayBuffer pour ce tableau qui référence les éléments du début \(inclus\) jusqu'à la fin \(exclus\).  
  
## Syntaxe  
  
```javascript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## Paramètres  
 `newInt8Array`  
 Sous\-tableau retourné par cette méthode.  
  
 `begin`  
 Index du début du tableau.  
  
 `end`  
 Index de la fin du tableau.  Il est non inclusif.  
  
## Notes  
 Si le paramètre de début ou de fin est négatif, il fait référence à un index de la fin du tableau, par opposition au début.  Si le paramètre de fin n'est pas spécifié, le sous\-tableau contient tous les éléments du début à la fin du TypedArray.  La plage spécifiée par les valeurs de début et de fin est ancrée à la plage d'index valide du tableau en cours.  Si la longueur calculée du nouveau TypedArray est négative, elle est ancrée à zéro.  Le TypedArray retourné est du même type que le tableau sur lequel cette méthode est appelée.  
  
## Exemple  
 L'exemple suivant montre comment obtenir un sous\-tableau comportant deux éléments, en commençant par le premier élément du tableau.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]