---
title: "Float64Array, objet | Microsoft Docs"
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
ms.assetid: 74c945dc-56ae-458c-b0aa-782f240e9b6c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Float64Array, objet
Tableau typé de valeurs float 64 bits.  Le contenu est initialisé à 0.  Si le nombre d'octets demandé ne peut pas être alloué, une exception est levée.  
  
## Syntaxe  
  
```  
  
float64Array = new Float64Array( length ); float64Array = new Float64Array( array ); float64Array = new Float64Array( buffer, byteOffset, length);  
```  
  
## Paramètres  
 `float64Array`  
 Requis.  Nom de la variable à laquelle l'objet **Float64Array** est assigné.  
  
 `length`  
 Spécifie le nombre d'éléments du tableau.  
  
 `array`  
 Tableau \(ou tableau typé\) contenu dans ce tableau.  Le contenu est initialisé conformément au contenu du tableau ou du tableau typé donné, chaque élément étant converti en type Float64.  
  
 `buffer`  
 ArrayBuffer représenté par Float64Array.  
  
 `byteOffset`  
 Facultatif.  Spécifie le décalage en octets à partir du début de la mémoire tampon auquel l'objet Float64Array doit commencer.  
  
 `length`  
 Nombre d'éléments dans le tableau.  
  
## Constantes  
 Le tableau suivant répertorie les constantes de l'objet `Float64Array`.  
  
|Constante|Description|  
|---------------|-----------------|  
|[Constante BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-float64array.md)|Taille en octets de chaque élément contenu dans le tableau.|  
  
## Propriétés  
 Le tableau suivant répertorie les constantes de l'objet `Float64Array`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Propriété buffer](../../javascript/reference/bytelength-property-float64array.md)|Lecture seule.  Obtient l'objet ArrayBuffer référencé par ce tableau.|  
|[Propriété byteLength](../../javascript/reference/bytelength-property-float64array.md)|Lecture seule.  Longueur en octets de ce tableau à partir du début de son ArrayBuffer, telle qu'elle est résolue au moment de la construction.|  
|[Propriété byteOffset](../../javascript/reference/length-property-float64array.md)|Lecture seule.  Offset en octets de ce tableau à partir du début de son ArrayBuffer, tel qu'il est résolu au moment de la construction.|  
|[Propriété length](../../javascript/reference/length-property-float64array.md)|Longueur du tableau.|  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Float64Array`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Méthode get](../../javascript/reference/get-method-float64array.md)|Omissible.  Obtient l'élément au niveau de l'index spécifié.|  
|[set, méthode \(Float64Array\)](../../javascript/reference/set-method-float64array.md)|Définit une valeur ou un tableau de valeurs.|  
|[subarray, méthode \(Float64Array\)](../../javascript/reference/subarray-method-float64array.md)|Obtient une nouvelle vue Float64Array du stockage ArrayBuffer pour ce tableau.|  
  
## Exemple  
 L'exemple suivant montre comment utiliser un objet Float64Array pour traiter les données binaires acquises via un XmlHttpRequest :  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Float64Array(buffer.byteLength / 8);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getFloat64(i * 8);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]