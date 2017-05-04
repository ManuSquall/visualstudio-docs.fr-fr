---
title: "Float32Array, objet | Microsoft Docs"
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
ms.assetid: 4b29456a-1488-4006-ae66-5bf4c05003b1
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Float32Array, objet
Tableau typé de valeurs float 32 bits.  Le contenu est initialisé à 0.  Si le nombre d'octets demandé ne peut pas être alloué, une exception est levée.  
  
## Syntaxe  
  
```  
  
float32Array = new Float32Array( length ); float32Array = new Float32Array( array ); float32Array = new Float32Array( buffer, byteOffset, length);  
```  
  
## Paramètres  
 `float32Array`  
 Requis.  Nom de la variable à laquelle l'objet **Float32Array** est assigné.  
  
 `length`  
 Spécifie le nombre d'éléments du tableau.  
  
 `array`  
 Tableau \(ou tableau typé\) contenu dans ce tableau.  Le contenu est initialisé conformément au contenu du tableau ou du tableau typé donné, chaque élément étant converti en type Float32.  
  
 `buffer`  
 ArrayBuffer représenté par Float32Array.  
  
 `byteOffset`  
 Facultatif.  Spécifie l'offset en octets à partir du début de la mémoire tampon auquel l'objet Float32Array doit commencer.  
  
 `length`  
 Nombre d'éléments dans le tableau.  
  
## Constantes  
 Le tableau suivant répertorie les constantes de l'objet `Float32Array`.  
  
|Constante|Description|  
|---------------|-----------------|  
|[Constante BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-float32array.md)|Taille en octets de chaque élément contenu dans le tableau.|  
  
## Propriétés  
 Le tableau suivant répertorie les constantes de l'objet `Float32Array`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Propriété buffer](../../javascript/reference/buffer-property-float32array.md)|Lecture seule.  Obtient l'objet ArrayBuffer référencé par ce tableau.|  
|[Propriété byteLength](../../javascript/reference/bytelength-property-float32array.md)|Lecture seule.  Longueur en octets de ce tableau à partir du début de son ArrayBuffer, telle qu'elle est résolue au moment de la construction.|  
|[Propriété byteOffset](../../javascript/reference/byteoffset-property-float32array.md)|Lecture seule.  Offset en octets de ce tableau à partir du début de son ArrayBuffer, tel qu'il est résolu au moment de la construction.|  
|[Propriété length](../../javascript/reference/length-property-float32array.md)|Longueur du tableau.|  
|||  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Float32Array`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Méthode get](../../javascript/reference/get-method-float32array.md)|Omissible.  Obtient l'élément au niveau de l'index spécifié.|  
|[set, méthode \(Float32Array\)](../../javascript/reference/set-method-float32array.md)|Définit une valeur ou un tableau de valeurs.|  
|[subarray, méthode \(Float32Array\)](../../javascript/reference/subarray-method-float32array.md)|Obtient une nouvelle vue Float32Array du stockage ArrayBuffer pour ce tableau.|  
  
## Exemple  
 L'exemple suivant montre comment utiliser un objet Float32Array pour traiter les données binaires acquises via un XmlHttpRequest :  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Float32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getFloat32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]