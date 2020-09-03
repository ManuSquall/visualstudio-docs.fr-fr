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
ms.openlocfilehash: 969f2bcb578d74ac02a7bdaa6984de5948e49e27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817604"
---
# <a name="date-object-expected"></a>Objet date attendu
Vous avez tenté d’appeler la méthode **date. prototype. ToString** ou **date. prototype. valueOf** sur un objet d’un type autre que `Date` . L’objet de ce type d’appel doit être de type `Date` . Par exemple :  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Appelez uniquement les méthodes **date. prototype. ToString** ou **date. prototype. valueOf** sur les objets de type `Date` .  
  
## <a name="see-also"></a>Voir aussi  
 [Objet date](../../javascript/reference/date-object-javascript.md)   
 [getDate, méthode (date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Objets intrinsèques](../../javascript/intrinsic-objects-javascript.md)