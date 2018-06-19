---
title: setint8, méthode (DataView) | Documents Microsoft
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
ms.assetid: 0a0e1450-e0c4-4778-8706-4d332442d882
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6f9bd9c4b3bea25686036d199d1a987927172d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639489"
---
# <a name="setint8-method-dataview"></a>setInt8, méthode (DataView)
Stocke une valeur Int8 à l’offset d’octet spécifié à partir du début de la vue.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
dataView.setInt8(byteOffset, value);   
```  
  
## <a name="parameters"></a>Paramètres  
 `byteOffset`  
 L’emplacement de la mémoire tampon à laquelle la valeur doit être définie.  
  
 `value`  
 Valeur à définir.  
  
## <a name="remarks"></a>Remarques  
 Ces méthodes déclenchent une exception si elles écririez au-delà de la fin de la vue.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment définir la première Int8 du DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setInt8(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]