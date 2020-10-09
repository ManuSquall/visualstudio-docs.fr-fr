---
title: "'Catch’attendu | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47411a6376cd843b3a12cf74ed1800775b98cd83
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861958"
---
# <a name="expected-catch"></a>'catch' attendu
Vous avez utilisé le bloc **try** de gestion des exceptions, mais n’avez pas écrit l’instruction **catch** associée. Le mécanisme de gestion des exceptions exige que le code qui peut échouer, ainsi que le code qui ne doit pas s’exécuter si une exception se produit, sont encapsulés à l’intérieur d’un bloc **try** . Les exceptions sont levées à partir du bloc **try** à l’aide de l’instruction **throw** et interceptées en dehors du bloc **try** avec une ou plusieurs instructions **catch** .  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajoutez le bloc **catch** associé.  
  
- Essayez d’utiliser un bloc **finally** au lieu d’un bloc **catch** .  
  
## <a name="see-also"></a>Voir aussi  
 [essayer... catch... Finally, instruction](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)   
 [Objet Error](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)