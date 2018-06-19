---
title: Uint8ClampedArray, objet (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51673eadc8eb905355bf136dc82b2f240462180a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642109"
---
# <a name="uint8clampedarray-object-javascript"></a>Uint8ClampedArray, objet (JavaScript)
Un tableau typé d'entiers non signés 8 bits avec des valeurs limitées à la plage 0-255. Le contenu est initialisé à 0. Si le nombre d'octets demandé ne peut pas être alloué, une exception est levée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      uint8ClampedArray = new Uint8ClampedArray( length );  
uint8ClampedArray = new Uint8ClampedArray( array );  
uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Paramètres  
 `uint8ClampedArray`  
 Obligatoire. Nom de la variable à laquelle l'objet `Uint8ClampedArray` est assigné.  
  
 `length`  
 Facultatif. Nombre d'éléments dans le tableau.  
  
 `array`  
 Facultatif. Tableau (ou tableau typé) contenu dans ce tableau. Le contenu est initialisé conformément au contenu du tableau ou du tableau typé donné, chaque élément étant converti en type `Uint8`.  
  
 `buffer`  
 Facultatif. Le [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) qui le `Uint8ClampedArray` représente.  
  
 `byteOffset`  
 Facultatif. Décalage en octets à partir du début de la mémoire tampon auquel l'objet `Uint8ClampedArray` doit commencer.  
  
 `length`  
 Facultatif. Nombre d’éléments dans le tableau.  
  
## <a name="remarks"></a>Remarques  
 Les valeurs stockées dans un objet `Uint8ClampedArray` sont comprises entre 0 et 255. Si vous définissez une valeur négative pour un membre du tableau, 0 est défini pour la valeur. Si vous définissez une valeur supérieure à 255, 255 est défini comme valeur.  
  
 Les valeurs dans un `Uint8ClampedArray` objet sont arrondies à la plus proche de la même valeur, qui est appelé arrondi bancaire.  
  
## <a name="constants"></a>Constantes  
 Le tableau suivant répertorie les constantes de l'objet `Uint8ClampedArray`.  
  
|Constante|Description|  
|--------------|-----------------|  
|[Bytes_per_element, constante](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|Taille en octets de chaque élément contenu dans le tableau.|  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les constantes de l'objet `Uint8ClampedArray`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[Buffer, propriété](../../javascript/reference/buffer-property-uint8clampedarray.md)|Lecture seule. Obtient le [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) qui est référencé par ce tableau.|  
|[ByteLength, propriété](../../javascript/reference/bytelength-property-uint8clampedarray.md)|Lecture seule. La longueur de ce tableau à partir du début de son [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), en octets, comme déterminé au moment de la construction.|  
|[byteoffset, propriété](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|Lecture seule. Le décalage de ce tableau à partir du début de son [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), en octets, comme déterminé au moment de la construction.|  
|[Length, propriété](../../javascript/reference/length-property-uint8clampedarray.md)|Longueur du tableau.|  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Uint8ClampedArray`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Set, méthode](../../javascript/reference/set-method-uint8clampedarray.md)|Définit une valeur ou un tableau de valeurs.|  
|[subarray, méthode](../../javascript/reference/subarray-method-uint8clampedarray.md)|Obtient un nouveau `Uint8ClampedArray` afficher de la [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) pour ce tableau, en spécifiant les premier et dernier éléments du sous-tableau.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser un objet `Uint8ClampedArray` pour traiter les données binaires acquises via `XmlHttpRequest` :  
  
```JavaScript  
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
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment les valeurs sont limitées dans un `Uint8ClampedArray`.  
  
```JavaScript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment les valeurs sont arrondies dans un `Uint8ClampedArray`.  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 12 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Uint8Array objet](../../javascript/reference/uint8array-object.md)   
 [Objet ArrayBuffer](../../javascript/reference/arraybuffer-object.md)
