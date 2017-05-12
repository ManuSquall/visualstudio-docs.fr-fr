---
title: "Int8Array, objet | Microsoft Docs"
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
ms.assetid: 0e3bdbc5-8d85-4c0d-b399-693b01674803
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Int8Array, objet
Tableau typé de valeurs entières de 8 bits.  Le contenu est initialisé à 0.  Si le nombre d'octets demandé ne peut pas être alloué, une exception est levée.  
  
## Syntaxe  
  
```  
  
      int8Array = new Int8Array( length );  
intArray = new Int8Array( array );  
intArray = new Int8Array( buffer, byteOffset, length);  
```  
  
## Paramètres  
 `int8Array`  
 Obligatoire.  Nom de la variable à laquelle l'objet `Int8Array` est assigné.  
  
 `length`  
 Spécifie le nombre d'éléments du tableau.  
  
 `array`  
 Tableau \(ou tableau typé\) contenu dans ce tableau.  Le contenu est initialisé conformément au contenu du tableau ou du tableau typé donné, chaque élément étant converti en type Int8.  
  
 `buffer`  
 ArrayBuffer représenté par Int8Array.  
  
 `byteOffset`  
 Facultatif.  Spécifie l'offset en octets à partir du début de la mémoire tampon auquel l'objet Int8Array doit commencer.  
  
 `length`  
 Nombre d'éléments dans le tableau.  
  
## Constantes  
 Le tableau suivant répertorie les constantes de l'objet `Int8Array`.  
  
|Constante|Description|  
|---------------|-----------------|  
|[Constante BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-int8array.md)|Taille en octets de chaque élément contenu dans le tableau.|  
  
## Propriétés  
 Le tableau suivant répertorie les constantes de l'objet `Int8Array`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Propriété buffer](../../javascript/reference/buffer-property-int8array.md)|Lecture seule.  Obtient l'objet ArrayBuffer référencé par ce tableau.|  
|[Propriété byteLength](../../javascript/reference/bytelength-property-int8array.md)|Lecture seule.  Longueur en octets de ce tableau à partir du début de son ArrayBuffer, telle qu'elle est résolue au moment de la construction.|  
|[Propriété byteOffset](../../javascript/reference/byteoffset-property-int8array.md)|Lecture seule.  Offset en octets de ce tableau à partir du début de son ArrayBuffer, tel qu'il est résolu au moment de la construction.|  
|[Propriété length](../../javascript/reference/length-property-int8array.md)|Longueur du tableau.|  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Int8Array`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[set, méthode \(Int8Array\)](../../javascript/reference/set-method-int8array.md)|Définit une valeur ou un tableau de valeurs.|  
|[subarray, méthode \(Int8Array\)](../../javascript/reference/subarray-method-int8array.md)|Obtient une nouvelle vue Int8Array du stockage ArrayBuffer pour ce tableau.|  
  
## Exemple  
 L'exemple suivant montre comment utiliser un objet Int8Array pour traiter les données binaires acquises via une requête XmlHttpRequest :  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int8Array(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]