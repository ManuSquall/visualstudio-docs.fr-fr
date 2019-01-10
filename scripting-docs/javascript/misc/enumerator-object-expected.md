---
title: Objet énumérateur attendu | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 002c3a748af8f7fa5c21109adcb279f893b38965
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093000"
---
# <a name="enumerator-object-expected"></a>Objet d'énumération attendu
Vous avez tenté d’appeler le **méthode Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** ou **Enumerator.prototype.moveNext** méthode sur un objet d’un autre type que `Enumerator`. L’objet de ce type d’appel doit être de type `Enumerator`. Voici un exemple de code qui enfreint cette règle :  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Appelez le **méthode Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, ou  **Enumerator.prototype.moveNext** méthodes sur des objets de type `Enumerator`. Pour déterminer si votre objet est un `Enumerator` de l’objet, utilisez :  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Enumerator](../../javascript/reference/enumerator-object-javascript.md)