---
description: Vous avez utilisé une instruction return dans la portée globale de votre code.
title: instruction’return’en dehors de la fonction | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c275db9b2b13f6730ef62a757502b1d51a59ee43
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571660"
---
# <a name="return-statement-outside-of-function"></a>Instruction 'return' en dehors de la fonction
Vous avez utilisé une `return` instruction dans la portée globale de votre code. L' `return` instruction ne doit apparaître que dans le corps d’une fonction.  
  
 L’appel d’une fonction avec l' `()` opérateur est une expression. Toutes les expressions ont des valeurs ; l' `return` instruction est utilisée pour spécifier la valeur retournée par une fonction. Le format général est le suivant :  
  
```js
  
return [ expression ];  
```  
  
 Lorsque l' `return` instruction est exécutée, l' *expression* est évaluée et retournée en tant que valeur de la fonction. S’il n’y a aucune expression, la non- **définition** est retournée.  
  
 L’exécution de la fonction s’arrête lorsque l' `return` instruction est exécutée, même s’il existe d’autres instructions encore dans le corps de la fonction. L’exception à cette règle est si l’instruction **Return** se produit dans un bloc **try** , et s’il existe un bloc **finally** correspondant, le code dans le bloc **finally** s’exécute avant le retour de la fonction.  
  
 Si une fonction retourne, car elle atteint la fin du corps de la fonction sans exécuter d' `return` instruction, la valeur retournée est la valeur **non définie** (cela signifie que le résultat de la fonction ne peut pas être utilisé dans le cadre d’une expression plus grande).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Supprimez l' `return` instruction du corps principal de votre code (portée globale).  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction return](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/return)   
 [Objet de fonction](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [Propriété caller (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/caller)
