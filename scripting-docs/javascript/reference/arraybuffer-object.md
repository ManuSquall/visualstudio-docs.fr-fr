---
title: Objet ArrayBuffer | Documents Microsoft
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c253d63d12a4a5e71d1661aae560b74debecdd62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="arraybuffer-object"></a>ArrayBuffer, objet
Représente une mémoire tampon brute de données binaires, qui est utilisée pour stocker les données pour les différents tableaux typés. `ArrayBuffers`Impossible de lire à partir d’ou écrits directement, mais ils peuvent être passés à un tableau typé ou [objet DataView](../../javascript/reference/dataview-object.md) pour interpréter la mémoire tampon brute en fonction des besoins.  
  
 Pour plus d’informations sur les tableaux typés, consultez [tableaux typés](../../javascript/advanced/typed-arrays-javascript.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## <a name="parameters"></a>Paramètres  
 `arrayBuffer`  
 Obligatoire. Nom de la variable à laquelle l'objet `ArrayBuffer` est assigné.  
  
 `length`  
 Longueur de la mémoire tampon. Le contenu du ArrayBuffer est initialisé à 0. Si le nombre d'octets demandé ne peut pas être alloué, une exception est levée.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `ArrayBuffer`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[ByteLength, propriété](../../javascript/reference/bytelength-property-arraybuffer.md)|Lecture seule. La longueur du ArrayBuffer (en octets).|  
  
## <a name="functions"></a>Fonctions  
 Le tableau suivant répertorie les fonctions de l'objet `ArrayBuffer`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[Arraybuffer.isview, fonction](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|Détermine si un objet fournit une vue de la mémoire tampon.|  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `ArrayBuffer`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[slice, méthode](../../javascript/reference/slice-method-arraybuffer.md)|Retourne une section d'un `ArrayBuffer`.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser un objet ArrayBuffer pour traiter les données binaires acquises via une [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx). Vous pouvez utiliser un [objet DataView](../../javascript/reference/dataview-object.md) pour obtenir les valeurs individuelles.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="remarks"></a>Remarques  
 Pour plus d’informations sur l’utilisation de `XmlHttpRequest`, consultez [améliorations de XMLHttpRequest](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069).  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]