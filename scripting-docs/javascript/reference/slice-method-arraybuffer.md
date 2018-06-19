---
title: slice, méthode (ArrayBuffer) | Documents Microsoft
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25fc10a02b4a3422a6720ad91c8bba29906da0e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640489"
---
# <a name="slice-method-arraybuffer"></a>slice, méthode (ArrayBuffer)
Retourne une section d’un [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Paramètres  
 `arrayBufferObj`  
 Obligatoire. Le [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) objet est copiée à partir de la section.  
  
 `start`  
 Obligatoire. Index d'octet du début de la section à copier.  
  
 `end`  
 Facultatif. Index d'octet de la fin de la section à copier.  
  
## <a name="remarks"></a>Remarques  
 Le `slice` méthode retourne un [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) objet qui contient la partie spécifiée des `arrayBufferObj`.  
  
 La méthode `slice` copie jusqu'à (sans l'inclure) l'octet indiqué par `end`. Si `start` ou `end` est négatif, l’index spécifié est traité comme `length`  +  `start` ou `end`, respectivement, où `length` est la longueur de la [ArrayBuffer](../../javascript/reference/arraybuffer-object.md). Si `end` est omis, l'extraction continue jusqu'à la fin de `arrayBufferObj`. Si `end` se produit avant `start`, aucun octet n’est copiés dans le nouveau [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent comment utiliser la méthode `slice`.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Objet ArrayBuffer](../../javascript/reference/arraybuffer-object.md)