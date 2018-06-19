---
title: SetUInt16, méthode (DataView) | Documents Microsoft
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
ms.assetid: bdf47cda-7fa5-4aaa-8aa2-8cf9a8d56cb3
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 935c117995e00284a0083a6bdf7aedfc8c51d15c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639699"
---
# <a name="setuint16-method-dataview"></a>setUint16, méthode (DataView)
Définit la valeur de Uint16 à l’offset d’octet spécifié à partir du début de la vue. Il n’existe aucune contrainte d’alignement ; les valeurs sur plusieurs octets peuvent être définies à n’importe quel décalage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
dataView.setUint16(byteOffset, value, littleEndian);   
```  
  
## <a name="parameters"></a>Paramètres  
 `testInt`  
 Obligatoire. Valeur Uint16 qui est retournée à partir de la méthode.  
  
 `value`  
 Valeur à définir.  
  
 `byteOffset`  
 L’emplacement de la mémoire tampon à laquelle la valeur doit être récupérée.  
  
 `littleEndian`  
 Facultatif. Si la valeur est false ou non définie, une valeur big-endian doit être écrits, sinon, une valeur de poids faible doit être écrit.  
  
## <a name="remarks"></a>Remarques  
 Ces méthodes déclenchent une exception si elles écririez au-delà de la fin de la vue.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment définir la première Uint16 dans le DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint16(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]