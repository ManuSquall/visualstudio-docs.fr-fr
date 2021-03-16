---
description: Vous avez tenté d’appeler la méthode date. prototype. toString ou date. prototype. valueOf sur un objet d’un type autre que date.
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
ms.openlocfilehash: 171514ae180c2e9b24e8aee56a23c47a909bd152
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571088"
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
 [Objet date](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date)   
 [getDate, méthode (date)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getdate)   
 [Objets intrinsèques](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)
