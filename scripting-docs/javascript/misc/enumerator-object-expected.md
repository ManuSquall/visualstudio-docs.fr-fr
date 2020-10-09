---
title: Objet énumérateur ATTENDU | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e63ee2970c90ffcfff5c02a384d3346b3ea6229
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862634"
---
# <a name="enumerator-object-expected"></a>Objet d'énumération attendu
Vous avez tenté d’appeler la méthode **Enumerator. prototype. atEnd, énumérateur. prototype. Item, Enumerator. prototype. MoveFirst** ou **Enumerator. prototype. MoveNext** sur un objet d’un type autre que `Enumerator` . L’objet de ce type d’appel doit être de type `Enumerator` . Voici un exemple de code qui interrompt cette règle :  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Appelez uniquement les méthodes **Enumerator. prototype. atEnd**, **énumérateur. prototype. Item**, **Enumerator. prototype. MoveFirst**ou **Enumerator. prototype. MoveNext** sur les objets de type `Enumerator` . Pour déterminer si votre objet est un `Enumerator` objet, utilisez :  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Enumerator](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)