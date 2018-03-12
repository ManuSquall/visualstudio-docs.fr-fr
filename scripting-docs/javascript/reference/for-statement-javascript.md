---
title: "pour l’instruction (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- for_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, for statements
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7142dbb8c00a351918d0821c3ca7dba3d7b2acb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="for-statement-javascript"></a>for, instruction (JavaScript)
Exécute un bloc d’instructions tant qu’une condition spécifiée a la valeur true.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## <a name="parameters"></a>Paramètres  
 `initialization`  
 Facultatif. d'une expression. Cette expression est exécutée une seule fois, avant l’exécution de la boucle.  
  
 `test`  
 Facultatif. Expression booléenne. Si `test` est `true`, `statement` est exécutée. Si `test` si `false`, la boucle se termine.  
  
 `increment`  
 Facultatif. d'une expression. L’expression d’incrémentation est exécutée à la fin de chaque passage dans la boucle.  
  
 `statement`  
 Facultatif. Une ou plusieurs instructions à exécuter si `test` est **true**. Il peut s'agir d'une instruction composée.  
  
## <a name="remarks"></a>Remarques  
 Vous utilisez généralement un `for` en boucle lors de la boucle est doit être exécutée un nombre déterminé de fois. A `for` boucle est utile pour itérer sur des tableaux et effectuer des traitements séquentiels.  
  
 Le test d’une expression conditionnelle se produit avant l’exécution de la boucle, par conséquent, un `for` instruction exécute zéro ou plusieurs fois.  
  
 Sur n’importe quelle ligne dans un `for` bloc d’instructions de boucle, vous pouvez utiliser la `break` instruction pour quitter la boucle, ou vous pouvez utiliser la `continue` instruction pour transférer le contrôle à la prochaine itération de la boucle.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la `for` instruction exécute les instructions délimitées comme suit :  
  
-   Tout d’abord, la valeur initiale de la variable `i` est évaluée.  
  
-   Ensuite, tant que la valeur de `i` est inférieure ou égale à 9, le `document.write` instructions sont exécutées et `i` est réévaluée.  
  
-   Lorsque `i` est supérieur à 9, la condition prend la valeur false et le contrôle est transféré à l’extérieur de la boucle.  
  
```JavaScript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## <a name="example"></a>Exemple  
 Toutes les expressions de la `for` instruction sont facultatifs. Dans l’exemple suivant, la `for` instructions créent une boucle infinie et un `break` instruction est utilisée pour quitter la boucle.  
  
```JavaScript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [instruction for... dans l’instruction](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instruction while](../../javascript/reference/while-statement-javascript.md)