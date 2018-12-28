---
title: instruction en dehors de la fonction ' return' | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a7c4b71938d960d3825030c42e965b6510ca575b
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802522"
---
# <a name="return-statement-outside-of-function"></a>Instruction 'return' en dehors de la fonction
Vous avez utilisé un `return` instruction dans la portée globale de votre code. La `return` instruction doit uniquement apparaître dans le corps d’une fonction.  
  
 Appel d’une fonction avec la `()` opérateur est une expression. Toutes les expressions ont des valeurs ; la `return` instruction est utilisée pour spécifier la valeur retournée par une fonction. Le format général est :  
  
```  
  
return [ expression ];  
```  
  
 Lorsque le `return` instruction est exécutée, *expression* est évaluée et retournée comme valeur de la fonction. Si aucune expression, **undefined** est retourné.  
  
 Exécution de la fonction s’arrête lorsque la `return` instruction est exécutée, même s’il existe toujours autres instructions dans le corps de fonction. L’exception à cette règle est si le **retourner** instruction s’exécute au sein d’un **essayez** bloc, et qu’il existe un correspondant **enfin** bloc, le code dans le  **enfin** bloc est exécutées avant que la fonction retourne.  
  
 Si une fonction retourne, car elle atteint la fin du corps de la fonction sans exécuter un `return` instruction, la valeur retournée est la **undefined** (ce qui signifie que le résultat de fonction ne peut pas être utilisé en tant que partie d’une expression plus longue ).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Supprimer la `return` instruction du corps principal de votre code (la portée globale).  
  
## <a name="see-also"></a>Voir aussi  
 [return, instruction](../../javascript/reference/return-statement-javascript.md)   
 [Objet de fonction](../../javascript/reference/function-object-javascript.md)   
 [Propriété caller (Function)](../../javascript/reference/caller-property-function-javascript.md)