---
title: continue, instruction (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- continue_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- continue statement
- loop structures, continue statement
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 391f919c4d06a6c529bfee34e21ca7238b3c63b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636379"
---
# <a name="continue-statement-javascript"></a>continue, instruction (JavaScript)
Arrête l'itération en cours d'une boucle et en lance une nouvelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
continue [label];  
```  
  
## <a name="remarks"></a>Remarques  
 Le paramètre facultatif `label` argument spécifie l’instruction à laquelle `continue` s’applique.  
  
 Vous pouvez utiliser la `continue` instruction uniquement dans un `while`, `do...while`, **pour**, ou `for...in` boucle. L’exécution de la `continue` instruction arrête l’itération actuelle de la boucle et poursuit le déroulement du programme avec le début de la boucle. Cela a les effets suivants sur les différents types de boucles :  
  
-   `while`et `do...while` boucles leur condition de test et si la valeur est true, réexécutez la boucle.  
  
-   `for`boucles exécutent leur expression d’incrémentation et, si l’expression de test est la valeur est true, exécutent à nouveau la boucle.  
  
-   `for...in`boucles passer au champ suivant de la variable spécifiée et réexécutez la boucle.  
  
## <a name="examples"></a>Exemples  
 Dans cet exemple, une boucle itère de 1 à 9. Les instructions entre `continue` et la fin de la `for` corps sont ignorés en raison de l’utilisation de la `continue` instruction avec l’expression `(i < 5)`.  
  
```JavaScript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 Dans le code suivant, le `continue` instruction fait référence à la `for` boucle est précédé par le `Inner:` étiquette. Lorsque `j` est 24, la `continue` qui provoque l’instruction `for` boucle à passer à l’itération suivante. Les nombres 21 à 23 et 25 à 30 impriment sur chaque ligne.  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [break, instruction](../../javascript/reference/break-statement-javascript.md)   
 [Instruction Do... while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Instruction for](../../javascript/reference/for-statement-javascript.md)   
 [instruction for... dans l’instruction](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instruction étiquetée](../../javascript/reference/labeled-statement-javascript.md)   
 [Instruction while](../../javascript/reference/while-statement-javascript.md)