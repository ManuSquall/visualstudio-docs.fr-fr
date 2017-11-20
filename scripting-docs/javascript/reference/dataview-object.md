---
title: Objet DataView | Documents Microsoft
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 370ee1afbdf7fe1d87843c4979833d54a575a4fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="dataview-object"></a>DataView, objet
Vous pouvez utiliser un objet DataView pour lire et écrire les différents types de données binaires à n’importe quel emplacement dans l’objet ArrayBuffer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dataView`  
 Obligatoire. Le nom de la variable à laquelle la **DataView** objet est assigné.  
  
 `buffer`  
 Arraybuffer représenté par l’objet DataView représente.  
  
 `byteOffset`  
 Facultatif. Spécifie le décalage en octets à partir du début de la mémoire tampon à laquelle le DataView doit commencer.  
  
 `byteLength`  
 Facultatif. Spécifie la longueur (en octets) de la section de la mémoire tampon qui doit être représentatif de DataView.  
  
## <a name="remarks"></a>Remarques  
 Si byteOffset et byteLength sont omis, le DataView s’étend sur toute la plage de ArrayBuffer. Si le byteLength est omis, le DataView étend la byteOffset donné jusqu'à la fin de l’objet ArrayBuffer. Si la donnée byteOffset et byteLength fait référence à une zone au-delà de la fin de l’objet ArrayBuffer, une exception est levée.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `DataView`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[Buffer, propriété](../../javascript/reference/buffer-property-dataview.md)|Lecture seule. Obtient l’objet ArrayBuffer référencé par cette vue.|  
|[ByteLength, propriété](../../javascript/reference/bytelength-property-dataview.md)|Lecture seule. Longueur en octets de cette vue à partir du début de son ArrayBuffer, telle qu'elle est résolue au moment de la construction.|  
|[byteoffset, propriété](../../javascript/reference/byteoffset-property-dataview.md)|Lecture seule. Le décalage de cette vue à partir du début de son ArrayBuffer, en octets, comme déterminé au moment de la construction.|  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `DataView`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[getint8, méthode](../../javascript/reference/getint8-method-dataview.md)|Obtient la valeur Int8 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode getUint8 (DataView)](../../javascript/reference/getuint8-method-dataview.md)|Obtient la valeur Uint8 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode getInt16 (DataView)](../../javascript/reference/getint16-method-dataview.md)|Obtient la valeur Int16 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode getUint16 (DataView)](../../javascript/reference/getuint16-method-dataview.md)|Obtient la valeur Uint16 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode getInt32 (DataView)](../../javascript/reference/getint32-method-dataview.md)|Obtient la valeur Int32 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode getUint32 (DataView)](../../javascript/reference/getuint32-method-dataview.md)|Obtient la valeur Uint32 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode getFloat32 (DataView)](../../javascript/reference/getfloat32-method-dataview.md)|Obtient la valeur Float32 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode getFloat64 (DataView)](../../javascript/reference/getfloat64-method-dataview.md)|Obtient la valeur Float64 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode setInt8 (DataView)](../../javascript/reference/setint8-method-dataview.md)|Stocke une valeur Int8 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode setUint8 (DataView)](../../javascript/reference/setuint8-method-dataview.md)|Stocke une valeur Uint8 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode setInt16 (DataView)](../../javascript/reference/setint16-method-dataview.md)|Stocke une valeur Int16 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode setUint16 (DataView)](../../javascript/reference/setuint16-method-dataview.md)|Stocke une valeur Uint16 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode setInt32 (DataView)](../../javascript/reference/setint32-method-dataview.md)|Stocke une valeur Int32 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode setUint32 (DataView)](../../javascript/reference/setuint32-method-dataview.md)|Stocke une valeur Uint32 égale à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode setFloat32 (DataView)](../../javascript/reference/setfloat32-method-dataview.md)|Stocke une valeur Float32 à l’offset d’octet spécifié à partir du début de la vue.|  
|[Méthode setFloat64 (DataView)](../../javascript/reference/setfloat64-method-dataview.md)|Stocke une valeur Float64 à l’offset d’octet spécifié à partir du début de la vue.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser un objet DataView à traiter les données binaires acquises via un XmlHttpRequest :  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var ints = new Int32Array(dataView.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]