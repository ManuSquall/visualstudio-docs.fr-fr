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
ms.openlocfilehash: ff61894ce808cd33876e876c596e791a3347ab72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817591"
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
 [Objet Enumerator](../../javascript/reference/enumerator-object-javascript.md)