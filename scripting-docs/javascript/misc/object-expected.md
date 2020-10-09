---
title: Objet ATTENDU | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a3b8510c92e15a5b1bf5e15bb774ba031f7181f
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862114"
---
# <a name="object-expected"></a>Objet attendu
Vous avez tenté d’appeler une méthode ou propriété sur un objet d’un type autre qu’`Object`, ou vous avez passé un argument d’un type autre qu’`Object` quand un `Object` était nécessaire.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Appelez la méthode ou propriété uniquement sur des objets de type `Object`.  
  
- Si l'erreur se produit pour un argument non-Object, passez un objet de type `Object`.  
  
- Vérifiez si une référence non définie ou null est appelée au lieu d'un objet de type `Object`.  
  
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
 [Objet Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)   
 [Objets et tableaux](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)