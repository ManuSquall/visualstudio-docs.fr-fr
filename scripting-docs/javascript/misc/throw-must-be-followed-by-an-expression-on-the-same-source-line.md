---
title: "' Throw ' doit être suivi par une expression sur la même ligne source | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 5d2989b2ebb5cf0095736d5667f85a807558c495
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841141"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>'Throw' doit être suivi d'une expression sur la même ligne source
Vous avez utilisé le `throw` mot clé, mais vous n’avez ne pas suivi il avec une expression sur la même ligne source. Un `throw` instruction se compose de deux parties : le `throw` mot clé, suivi par l’expression devant être levé. Exemple :  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Vous ne pouvez pas diviser ces deux composants.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assurez-vous que le `throw` mot clé et l’expression à être levée s’affiche sur la même ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’erreur](../../javascript/reference/error-object-javascript.md)   
 [Throw (instruction)](../../javascript/reference/throw-statement-javascript.md)   
 [Instruction try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)