---
title: Objet de Float64Array | Documents Microsoft
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
ms.assetid: 74c945dc-56ae-458c-b0aa-782f240e9b6c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20544812d94c1234d85d714f6e469d0de4f4c5ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637409"
---
# <a name="float64array-object"></a>Float64Array, objet
Tableau typé de valeurs float 64 bits. Le contenu est initialisé à 0. Si le nombre d'octets demandé ne peut pas être alloué, une exception est levée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      float64Array = new Float64Array( length );  
float64Array = new Float64Array( array );  
float64Array = new Float64Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Paramètres  
 `float64Array`  
 Obligatoire. Le nom de la variable à laquelle la **Float64Array** objet est assigné.  
  
 `length`  
 Spécifie le nombre d'éléments du tableau.  
  
 `array`  
 Tableau (ou tableau typé) contenu dans ce tableau. Le contenu est initialisé conformément au contenu du tableau ou du tableau typé donné, chaque élément étant converti en type Float64.  
  
 `buffer`  
 ArrayBuffer représenté par Float64Array.  
  
 `byteOffset`  
 Facultatif. Spécifie le décalage en octets à partir du début de la mémoire tampon auquel l'objet Float64Array doit commencer.  
  
 `length`  
 Nombre d'éléments dans le tableau.  
  
## <a name="constants"></a>Constantes  
 Le tableau suivant répertorie les constantes de l'objet `Float64Array`.  
  
|Constante|Description|  
|--------------|-----------------|  
|[Bytes_per_element, constante](../../javascript/reference/bytes-per-element-constant-float64array.md)|Taille en octets de chaque élément contenu dans le tableau.|  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les constantes de l'objet `Float64Array`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[Buffer, propriété](../../javascript/reference/bytelength-property-float64array.md)|Lecture seule. Obtient l'objet ArrayBuffer référencé par ce tableau.|  
|[ByteLength, propriété](../../javascript/reference/bytelength-property-float64array.md)|Lecture seule. Longueur en octets de ce tableau à partir du début de son ArrayBuffer, telle qu'elle est résolue au moment de la construction.|  
|[byteoffset, propriété](../../javascript/reference/length-property-float64array.md)|Lecture seule. Offset en octets de ce tableau à partir du début de son ArrayBuffer, tel qu'il est résolu au moment de la construction.|  
|[Length, propriété](../../javascript/reference/length-property-float64array.md)|Longueur du tableau.|  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Float64Array`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Get (méthode)](../../javascript/reference/get-method-float64array.md)|Omissible. Obtient l'élément au niveau de l'index spécifié.|  
|[Méthode set (Float64Array)](../../javascript/reference/set-method-float64array.md)|Définit une valeur ou un tableau de valeurs.|  
|[Méthode subarray (Float64Array)](../../javascript/reference/subarray-method-float64array.md)|Obtient une nouvelle vue Float64Array du stockage ArrayBuffer pour ce tableau.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser un objet Float64Array pour traiter les données binaires acquises via un XmlHttpRequest :  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]