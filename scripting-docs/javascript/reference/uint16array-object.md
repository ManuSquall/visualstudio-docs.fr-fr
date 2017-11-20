---
title: Objet de Uint16Array | Documents Microsoft
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
ms.assetid: e684647d-04d0-41a9-9089-16612e18ec7d
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 447c0509a29f1696e0204d6f37ff88d3c0bdecae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="uint16array-object"></a>Uint16Array, objet
Un tableau typé de valeurs de l’entier non signé 16 bits. Le contenu est initialisé à 0. Si le nombre d'octets demandé ne peut pas être alloué, une exception est levée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      uint16Array = new Uint16Array( length );  
uint16Array = new Uint16Array( array );  
uint16Array = new Uint16Array( buffer, byteOffset, length );  
```  
  
## <a name="parameters"></a>Paramètres  
 `uint16Array`  
 Obligatoire. Le nom de la variable à laquelle la **Uint16Array** objet est assigné.  
  
 `length`  
 Spécifie le nombre d'éléments du tableau.  
  
 `array`  
 Tableau (ou tableau typé) contenu dans ce tableau. Le contenu est initialisé conformément au contenu du tableau ou du tableau typé donné, chaque élément étant converti en type Uint16.  
  
 `buffer`  
 ArrayBuffer représenté par Uint16Array.  
  
 `byteOffset`  
 Facultatif. Spécifie l'offset en octets à partir du début de la mémoire tampon auquel l'objet Uint16Array doit commencer.  
  
 `length`  
 Nombre d’éléments dans le tableau.  
  
## <a name="constants"></a>Constantes  
 Le tableau suivant répertorie les constantes de l'objet `Uint16Array`.  
  
|Constante|Description|  
|--------------|-----------------|  
|[Bytes_per_element, constante](../../javascript/reference/bytes-per-element-constant-uint16array.md)|Taille en octets de chaque élément contenu dans le tableau.|  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les constantes de l'objet `Uint16Array`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[Buffer, propriété](../../javascript/reference/buffer-property-uint16array.md)|Lecture seule. Obtient l'objet ArrayBuffer référencé par ce tableau.|  
|[ByteLength, propriété](../../javascript/reference/bytelength-property-uint16array.md)|Lecture seule. Longueur en octets de ce tableau à partir du début de son ArrayBuffer, telle qu'elle est résolue au moment de la construction.|  
|[byteoffset, propriété](../../javascript/reference/byteoffset-property-uint16array.md)|Lecture seule. Offset en octets de ce tableau à partir du début de son ArrayBuffer, tel qu'il est résolu au moment de la construction.|  
|[Length, propriété](../../javascript/reference/length-property-uint16array.md)|Longueur du tableau.|  
|||  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Uint16Array`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Méthode set (Uint16Array)](../../javascript/reference/set-method-uint16array.md)|Définit une valeur ou un tableau de valeurs.|  
|[Méthode subarray (Uint16Array)](../../javascript/reference/subarray-method-uint16array.md)|Obtient une nouvelle vue Uint16Array du stockage ArrayBuffer pour ce tableau.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser un objet Uint16Array pour traiter les données binaires acquises via une requête XmlHttpRequest :  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]