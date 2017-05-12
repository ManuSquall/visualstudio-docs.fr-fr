---
title: "set, m&#233;thode (Int8Array) | Microsoft Docs"
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
ms.assetid: 4beae82e-8556-48aa-86c6-18c8859d913e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# set, m&#233;thode (Int8Array)
Définit une valeur ou un tableau de valeurs.  
  
## Syntaxe  
  
```javascript  
int8Array.set(index, value);  
int8Array.set(array, offset);  
  
```  
  
## Paramètres  
 `index`  
 Index de l'emplacement à définir.  
  
 `value`  
 Valeur à définir.  
  
 `array`  
 Tableau typé ou non typé de valeurs à définir.  
  
 `offset`  
 Index dans le tableau en cours au niveau duquel les valeurs doivent être écrites.  
  
## Notes  
 Si le tableau d'entrée est un TypedArray, les deux tableaux peuvent utiliser le même ArrayBuffer sous\-jacent.  Dans cette situation, les valeurs sont définies comme si toutes les données étaient d'abord copiées dans une mémoire tampon temporaire qui ne chevauche pas les tableaux, puis les données de la mémoire tampon temporaire étaient copiées dans le tableau en cours.  
  
 Si l'offset plus la longueur du tableau donné sont en dehors des limites du TypedArray en cours, une exception est levée.  
  
## Exemple  
 L'exemple suivant montre comment définir le premier élément du tableau.  
  
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
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]