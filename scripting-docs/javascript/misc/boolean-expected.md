---
title: "Booléen attendu | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 600ab26f60c2196ebc682adcffcd6b24c23cd358
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-expected"></a>Booléen attendu
Vous avez tenté d’appeler le **Boolean.prototype.toString** ou **Boolean.prototype.valueOf** méthode sur un objet d’un type autre que `Boolean`. L’objet de ce type d’appel doit être de type `Boolean`. Exemple :  
  
```JavaScript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Appelez uniquement le booléen**. prototype.toString** ou **Boolean.prototype.valueOf** méthodes sur des objets de type **booléenne.**  
  
## <a name="see-also"></a>Voir aussi  
 [Boolean (objet)](../../javascript/reference/boolean-object-javascript.md)   
 [Types de données](../../javascript/data-types-javascript.md)   
 [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)   
 [Copie, passage et comparaison de données](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)