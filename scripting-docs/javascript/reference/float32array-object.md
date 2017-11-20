---
title: Objet de Float32Array | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4b29456a-1488-4006-ae66-5bf4c05003b1
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f7ef022b43179d2d9ce3f88fc78b8854d3cea62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="float32array-object"></a>Float32Array, objet
Tableau typé de valeurs float 32 bits. Le contenu est initialisé à 0. Si le nombre d'octets demandé ne peut pas être alloué, une exception est levée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      float32Array = new Float32Array( length );  
float32Array = new Float32Array( array );  
float32Array = new Float32Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Paramètres  
 `float32Array`  
 Obligatoire. Le nom de la variable à laquelle la **Float32Array** objet est assigné.  
  
 `length`  
 Spécifie le nombre d'éléments du tableau.  
  
 `array`  
 Tableau (ou tableau typé) contenu dans ce tableau. Le contenu est initialisé conformément au contenu du tableau ou du tableau typé donné, chaque élément étant converti en type Float32.  
  
 `buffer`  
 ArrayBuffer représenté par Float32Array.  
  
 `byteOffset`  
 Facultatif. Spécifie l'offset en octets à partir du début de la mémoire tampon auquel l'objet Float32Array doit commencer.  
  
 `length`  
 Nombre d'éléments dans le tableau.  
  
## <a name="constants"></a>Constantes  
 Le tableau suivant répertorie les constantes de l'objet `Float32Array`.  
  
|Constante|Description|  
|--------------|-----------------|  
|[Bytes_per_element, constante](../../javascript/reference/bytes-per-element-constant-float32array.md)|Taille en octets de chaque élément contenu dans le tableau.|  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les constantes de l'objet `Float32Array`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[Buffer, propriété](../../javascript/reference/buffer-property-float32array.md)|Lecture seule. Obtient l'objet ArrayBuffer référencé par ce tableau.|  
|[ByteLength, propriété](../../javascript/reference/bytelength-property-float32array.md)|Lecture seule. Longueur en octets de ce tableau à partir du début de son ArrayBuffer, telle qu'elle est résolue au moment de la construction.|  
|[byteoffset, propriété](../../javascript/reference/byteoffset-property-float32array.md)|Lecture seule. Offset en octets de ce tableau à partir du début de son ArrayBuffer, tel qu'il est résolu au moment de la construction.|  
|[Length, propriété](../../javascript/reference/length-property-float32array.md)|Longueur du tableau.|  
|||  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Float32Array`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Get (méthode)](../../javascript/reference/get-method-float32array.md)|Omissible. Obtient l'élément au niveau de l'index spécifié.|  
|[Méthode set (Float32Array)](../../javascript/reference/set-method-float32array.md)|Définit une valeur ou un tableau de valeurs.|  
|[Méthode subarray (Float32Array)](../../javascript/reference/subarray-method-float32array.md)|Obtient une nouvelle vue Float32Array du stockage ArrayBuffer pour ce tableau.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser un objet Float32Array pour traiter les données binaires acquises via un XmlHttpRequest :  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]