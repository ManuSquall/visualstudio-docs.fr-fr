---
title: "GetUInt16, méthode (DataView) | Documents Microsoft"
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
ms.assetid: 3c0d9ad8-30b0-42a3-b0fe-aa805398c396
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2da1ea7bdbbbc1d99f9b7b6c33e4b3d83e0ba84f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="getuint16-method-dataview"></a>getUint16, méthode (DataView)
Obtient la valeur Uint16 à l’offset d’octet spécifié à partir du début de la vue. Il n’existe aucune contrainte d’alignement ; les valeurs sur plusieurs octets peuvent être lues à partir de n’importe quel décalage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
var testInt = dataView.getUint16(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Paramètres  
 `testInt`  
 Obligatoire. Valeur Uint16 qui est retournée à partir de la méthode.  
  
 `byteOffset`  
 L’emplacement de la mémoire tampon à laquelle la valeur doit être récupérée.  
  
 `littleEndian`  
 Facultatif. Si la valeur est false ou non définie, une valeur big-endian doit être lue, sinon, une valeur de poids faible doit être lue.  
  
## <a name="remarks"></a>Remarques  
 Ces méthodes déclenchent une exception si elles sont en lecture au-delà de la fin de la vue.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment obtenir le premier Uint16 dans le DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getUint16(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]