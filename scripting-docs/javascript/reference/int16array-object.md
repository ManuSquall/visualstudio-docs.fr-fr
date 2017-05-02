---
title: "Int16Array, objet | Microsoft Docs"
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
ms.assetid: b87f36b4-4e38-4f32-b258-654c4ad2c615
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Int16Array, objet
Tableau typé de valeurs entières de 16 bits.  Le contenu est initialisé à 0.  Si le nombre d'octets demandé ne peut pas être alloué, une exception est levée.  
  
## Syntaxe  
  
```  
  
      int16Array = new Int16Array( length );  
int16Array = new Int16Array( array );  
int16Array = new Int16Array( buffer, byteOffset, length);  
```  
  
## Paramètres  
 `int16Array`  
 Obligatoire.  Nom de la variable à laquelle l'objet **Int16Array** est assigné.  
  
 `length`  
 Spécifie le nombre d'éléments du tableau.  
  
 `array`  
 Tableau \(ou tableau typé\) contenu dans ce tableau.  Le contenu est initialisé conformément au contenu du tableau ou du tableau typé donné, chaque élément étant converti en type Int16.  
  
 `buffer`  
 ArrayBuffer représenté par Int16Array.  
  
 `byteOffset`  
 Facultatif.  Spécifie l'offset en octets à partir du début de la mémoire tampon auquel l'objet Int16Array doit commencer.  
  
 `length`  
 Nombre d'éléments dans le tableau.  
  
## Constantes  
 Le tableau suivant répertorie les constantes de l'objet `Int16Array`.  
  
|Constante|Description|  
|---------------|-----------------|  
|[Constante BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-int16array.md)|Taille en octets de chaque élément contenu dans le tableau.|  
  
## Propriétés  
 Le tableau suivant répertorie les constantes de l'objet `Int16Array`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Propriété buffer](../../javascript/reference/buffer-property-int16array.md)|Lecture seule.  Obtient l'objet ArrayBuffer référencé par ce tableau.|  
|[Propriété byteLength](../../javascript/reference/byteoffset-property-int16array.md)|Lecture seule.  Longueur en octets de ce tableau à partir du début de son ArrayBuffer, telle qu'elle est résolue au moment de la construction.|  
|[Propriété byteOffset](../../javascript/reference/byteoffset-property-int16array.md)|Lecture seule.  Offset en octets de ce tableau à partir du début de son ArrayBuffer, tel qu'il est résolu au moment de la construction.|  
|[Propriété length](../../javascript/reference/length-property-int16array.md)|Longueur du tableau.|  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Int16Array`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[set, méthode \(Int16Array\)](../../javascript/reference/set-method-int16array.md)|Définit une valeur ou un tableau de valeurs.|  
|[subarray, méthode \(Int16Array\)](../../javascript/reference/subarray-method-int16array.md)|Obtient une nouvelle vue Int16Array du stockage ArrayBuffer pour ce tableau.|  
  
## Exemple  
 L'exemple suivant montre comment utiliser un objet Int16Array pour traiter les données binaires acquises via une requête XmlHttpRequest :  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]