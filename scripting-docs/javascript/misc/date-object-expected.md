---
title: Objet date attendu | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 28531c1ac1dc73ca2bf309d412b08d23dd17bfb8
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862649"
---
# <a name="date-object-expected"></a>Objet date attendu
Vous avez tenté d’appeler la méthode **date. prototype. ToString** ou **date. prototype. valueOf** sur un objet d’un type autre que `Date` . L’objet de ce type d’appel doit être de type `Date` . Exemple :  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Appelez uniquement les méthodes **date. prototype. ToString** ou **date. prototype. valueOf** sur les objets de type `Date` .  
  
## <a name="see-also"></a>Voir aussi  
 [Objet date](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date)   
 [getDate, méthode (date)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getdate)   
 [Objets intrinsèques](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)