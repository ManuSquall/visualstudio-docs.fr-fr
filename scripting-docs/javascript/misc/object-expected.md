---
title: Objet attendu | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6add25325653627d23eb699ab53c0f2799c8322f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632809"
---
# <a name="object-expected"></a>Objet attendu
Vous avez tenté d'appeler une méthode ou propriété sur un objet d'un type autre qu'`Object`, ou vous avez passé un argument d'un type autre qu'`Object` quand un `Object` était nécessaire.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Appelez la méthode ou propriété uniquement sur des objets de type `Object`.  
  
-   Si l'erreur se produit pour un argument non-Object, passez un objet de type `Object`.  
  
-   Vérifiez si une référence non définie ou null est appelée au lieu d'un objet de type `Object`.  
  
     Par exemple, si vous obtenez cette erreur sur myVar dans le code suivant :  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     vous pouvez utiliser ce code à la place :  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Object (objet)](../../javascript/reference/object-object-javascript.md)   
 [Objets et tableaux](../../javascript/objects-and-arrays-javascript.md)