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
ms.openlocfilehash: 2767ffc16b637c6b1e7bdf51cb0815d71f58edac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946379"
---
# <a name="date-object-expected"></a>Objet date attendu
Vous avez tenté d’appeler le **Date.prototype.toString** ou **Date.prototype.valueOf** méthode sur un objet d’un type autre que `Date`. L’objet de ce type d’appel doit être de type `Date`. Exemple :  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Appelez le **Date.prototype.toString** ou **Date.prototype.valueOf** méthodes sur des objets de type `Date`.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Date](../../javascript/reference/date-object-javascript.md)   
 [GETDATE, méthode (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Objets intrinsèques](../../javascript/intrinsic-objects-javascript.md)