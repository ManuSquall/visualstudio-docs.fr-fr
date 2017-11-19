---
title: "setfloat64, méthode (DataView) | Documents Microsoft"
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
ms.assetid: 63d2c631-876f-4d4b-b3b6-62b0aaffe6c5
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e22552e4190c74b520dfce853be6e9d1364764e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="setfloat64-method-dataview"></a>setFloat64, méthode (DataView)
Définit la valeur Float64 à l’offset d’octet spécifié à partir du début de la vue. Il n’existe aucune contrainte d’alignement ; les valeurs sur plusieurs octets peuvent être définies à n’importe quel décalage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
dataView.setFloat64 (byteOffset, value, littleEndian);   
```  
  
## <a name="parameters"></a>Paramètres  
 `byteOffset`  
 L’emplacement de la mémoire tampon à laquelle la valeur doit être récupérée.  
  
 `value`  
 Valeur à définir.  
  
 `littleEndian`  
 Facultatif. Si la valeur est false ou non définie, une valeur big-endian doit être écrits, sinon, une valeur de poids faible doit être écrit.  
  
## <a name="remarks"></a>Remarques  
 Ces méthodes déclenchent une exception si elles écririez au-delà de la fin de la vue.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment définir la première Float64 du DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setFloat64(0, 9.1);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]