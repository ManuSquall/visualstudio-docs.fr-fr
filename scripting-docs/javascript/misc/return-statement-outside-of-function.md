---
title: '&#39; retour &#39; instruction en dehors de la fonction | Documents Microsoft'
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
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07b633c87dc11b291a5a5783f8121b2a368996d6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="39return39-statement-outside-of-function"></a>&#39; retour &#39; instruction en dehors de la fonction
Vous avez utilisé un `return` instruction dans la portée globale de votre code. La `return` instruction ne doit apparaître dans le corps d’une fonction.  
  
 Appel d’une fonction avec la `()` opérateur est une expression. Toutes les expressions ont des valeurs ; la `return` instruction est utilisée pour spécifier la valeur retournée par une fonction. La forme générale est la suivante :  
  
```  
  
return [ expression ];  
```  
  
 Lorsque le `return` instruction est exécutée, *expression* est évaluée et retournée comme valeur de la fonction. Si aucune expression, **non défini** est retourné.  
  
 Exécution de la fonction s’arrête lorsque la `return` instruction est exécutée, même s’il existe toujours autres instructions dans le corps de la fonction. L’exception à cette règle est si le **retourner** instruction se produit dans un **essayez** bloc, et qu’il existe un correspondant **enfin** bloquer le code le  **enfin** bloc s’exécute avant le retour de la fonction.  
  
 Si une fonction retourne, car il atteint la fin du corps de la fonction sans avoir exécuté un `return` instruction, la valeur renvoyée est la **non défini** (ce qui signifie que le résultat de fonction ne peut pas être utilisé en tant que partie d’une plus grande expression ).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Supprimer la `return` instruction du corps principal de votre code (la portée globale).  
  
## <a name="see-also"></a>Voir aussi  
 [return, instruction](../../javascript/reference/return-statement-javascript.md)   
 [Objet de fonction](../../javascript/reference/function-object-javascript.md)   
 [Propriété caller (Function)](../../javascript/reference/caller-property-function-javascript.md)