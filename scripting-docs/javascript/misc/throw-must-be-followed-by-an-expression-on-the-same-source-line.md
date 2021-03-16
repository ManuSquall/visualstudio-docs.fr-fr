---
description: Vous avez utilisé le mot clé throw, mais vous ne l’avez pas suivi d’une expression sur la même ligne source.
title: Throw doit être suivi d’une expression sur la même ligne source | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfa2bace6f82ae972204cc0a405cc7e8682e98af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570711"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>'Throw' doit être suivi d'une expression sur la même ligne source
Vous avez utilisé le `throw` mot clé, mais vous ne l’avez pas suivi d’une expression sur la même ligne source. Une `throw` instruction se compose de deux parties : le `throw` mot clé, suivi de l’expression à lever. Par exemple :  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Vous ne pouvez pas fractionner ces deux composants.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Assurez-vous que le `throw` mot clé et l’expression à lever apparaissent sur la même ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Error](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [Throw (instruction)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [essayer... catch... Finally, instruction](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)
