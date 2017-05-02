---
title: "ArrayBuffer, objet | Microsoft Docs"
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# ArrayBuffer, objet
Représente une mémoire tampon brute de données binaires, qui est utilisée pour stocker les données pour les différents tableaux typés.  Les `ArrayBuffers` ne peuvent pas être lus ou écrits directement, mais ils peuvent être passés à un tableau typé ou [DataView, objet](../../javascript/reference/dataview-object.md) pour interpréter la mémoire tampon brute quand cela est nécessaire.  
  
 Pour plus d'informations sur les tableaux typés, voir [Tableaux typés](../../javascript/advanced/typed-arrays-javascript.md).  
  
## Syntaxe  
  
```javascript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## Paramètres  
 `arrayBuffer`  
 Requis.  Nom de la variable à laquelle l'objet `ArrayBuffer` est assigné.  
  
 `length`  
 Longueur de la mémoire tampon.  Le contenu du ArrayBuffer est initialisé à 0.  Si le nombre d'octets demandé ne peut pas être alloué, une exception est levée.  
  
## Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `ArrayBuffer`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Propriété byteLength](../../javascript/reference/bytelength-property-arraybuffer.md)|Lecture seule.  La longueur du ArrayBuffer \(en octets\).|  
  
## Fonctions  
 Le tableau suivant répertorie les fonctions de l'objet `ArrayBuffer`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Fonction ArrayBuffer.isView](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|Détermine si un objet fournit une vue de la mémoire tampon.|  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `ArrayBuffer`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Méthode slice](../../javascript/reference/slice-method-arraybuffer.md)|Retourne une section d'un `ArrayBuffer`.|  
  
## Exemple  
 L'exemple suivant montre comment utiliser un objet ArrayBuffer pour traiter les données binaires acquises de [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx).  Vous pouvez utiliser un [DataView, objet](../../javascript/reference/dataview-object.md) pour obtenir les valeurs individuelles.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Notes  
 Pour plus d'informations sur l'utilisation de `XmlHttpRequest`, voir [XMLHttpRequest enhancements](http://msdn.microsoft.com/fr-fr/be09137c-6546-441b-b953-dcbf72b77069).  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]