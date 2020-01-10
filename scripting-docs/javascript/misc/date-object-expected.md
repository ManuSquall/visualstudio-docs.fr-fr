---
title: Objet date attendu | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 10af48c4804df3b5513df71578b948abe73ff8c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572903"
---
# <a name="date-object-expected"></a>Objet date attendu
Vous avez tenté d’appeler la méthode **date. prototype. ToString** ou **date. prototype. valueOf** sur un objet d’un type autre que `Date`. L’objet de ce type d’appel doit être de type `Date`. Exemple :  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Appelez uniquement les méthodes **date. prototype. ToString** ou **date. prototype. valueOf** sur les objets de type `Date`.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Date](../../javascript/reference/date-object-javascript.md)   
 [GETDATE, méthode (date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Objets intrinsèques](../../javascript/intrinsic-objects-javascript.md)