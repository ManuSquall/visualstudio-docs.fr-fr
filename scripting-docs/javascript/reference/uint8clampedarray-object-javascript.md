---
title: "Uint8ClampedArray, objet (JavaScript) | Microsoft Docs"
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
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Uint8ClampedArray, objet (JavaScript)
Un tableau typé d'entiers non signés 8 bits avec des valeurs limitées à la plage 0\-255.  Le contenu est initialisé à 0.  Si le nombre d'octets demandé ne peut pas être alloué, une exception est levée.  
  
## Syntaxe  
  
```  
  
uint8ClampedArray = new Uint8ClampedArray( length ); uint8ClampedArray = new Uint8ClampedArray( array ); uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## Paramètres  
 `uint8ClampedArray`  
 Requis.  Nom de la variable à laquelle l'objet `Uint8ClampedArray` est assigné.  
  
 `length`  
 Facultatif.  Nombre d'éléments dans le tableau.  
  
 `array`  
 Facultatif.  Tableau \(ou tableau typé\) contenu dans ce tableau.  Le contenu est initialisé conformément au contenu du tableau ou du tableau typé donné, chaque élément étant converti en type `Uint8`.  
  
 `buffer`  
 Facultatif.  [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) représenté par `Uint8ClampedArray`.  
  
 `byteOffset`  
 Facultatif.  Décalage en octets à partir du début de la mémoire tampon auquel l'objet `Uint8ClampedArray` doit commencer.  
  
 `length`  
 Facultatif.  Nombre d'éléments dans le tableau.  
  
## Notes  
 Les valeurs stockées dans un objet `Uint8ClampedArray` sont comprises entre 0 et 255.  Si vous définissez une valeur négative pour un membre du tableau, 0 est défini pour la valeur.  Si vous définissez une valeur supérieure à 255, 255 est défini comme valeur.  
  
 Les valeurs dans un objet `Uint8ClampedArray` sont arrondies à la valeur de l'événement la plus proche, appelé arrondi bancaire.  
  
## Constantes  
 Le tableau suivant répertorie les constantes de l'objet `Uint8ClampedArray`.  
  
|Constante|Description|  
|---------------|-----------------|  
|[Constante BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|Taille en octets de chaque élément contenu dans le tableau.|  
  
## Propriétés  
 Le tableau suivant répertorie les constantes de l'objet `Uint8ClampedArray`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Propriété buffer](../../javascript/reference/buffer-property-uint8clampedarray.md)|Lecture seule.  Obtient l'objet [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) référencé par ce tableau.|  
|[Propriété byteLength](../../javascript/reference/bytelength-property-uint8clampedarray.md)|Lecture seule.  Longueur en octets de ce tableau à partir du début de son [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), telle qu'elle est définie au moment de la construction.|  
|[Propriété byteOffset](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|Lecture seule.  Décalage en octets de ce tableau à partir du début de son [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), telle qu'il est défini au moment de la construction.|  
|[Propriété length](../../javascript/reference/length-property-uint8clampedarray.md)|Longueur du tableau.|  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Uint8ClampedArray`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Méthode set](../../javascript/reference/set-method-uint8clampedarray.md)|Définit une valeur ou un tableau de valeurs.|  
|[Méthode subarray](../../javascript/reference/subarray-method-uint8clampedarray.md)|Obtient une nouvelle vue `Uint8ClampedArray` du [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) stocké pour ce tableau, spécifiant le premier et le dernier membre du sous\-tableau.|  
  
## Exemple  
 L'exemple suivant montre comment utiliser un objet `Uint8ClampedArray` pour traiter les données binaires acquises via `XmlHttpRequest` :  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8ClampedArray(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Exemple  
 L'exemple suivant montre comment les valeurs sont limitées dans un `Uint8ClampedArray`.  
  
```javascript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## Exemple  
 L'exemple suivant montre comment les valeurs sont arrondies dans un `Uint8ClampedArray`.  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 11 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Voir aussi  
 [Uint8Array, objet](../../javascript/reference/uint8array-object.md)   
 [ArrayBuffer, objet](../../javascript/reference/arraybuffer-object.md)