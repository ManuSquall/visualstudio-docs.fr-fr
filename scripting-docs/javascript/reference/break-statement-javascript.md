---
title: break, instruction (JavaScript) | Documents Microsoft
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
- break_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- break statement
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f085a4e51309bf9a060e9ffa352c6ae85924237
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634149"
---
# <a name="break-statement-javascript"></a>break, instruction (JavaScript)
Met fin à la boucle actuelle, ou si conjointement avec un `label`, termine l’instruction associée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
break [label];  
```  
  
## <a name="remarks"></a>Remarques  
 Le paramètre facultatif `label` argument spécifie l’étiquette de l’instruction que vous interrompez.  
  
 Vous utilisez généralement la `break` instruction `switch` instructions et dans `while`, `for`, `for...in`, ou `do...while` boucles. Vous utilisez généralement la `label` argument dans `switch` instructions, mais il peut être utilisé dans n’importe quelle instruction, simple ou composée.  
  
 L’exécution de la `break` instruction quitte la boucle actuelle ou l’instruction et commence l’exécution du script avec l’instruction qui suit immédiatement.  
  
## <a name="examples"></a>Exemples  
 Dans cet exemple, le compteur est configuré pour compter de 1 à 99 ; Toutefois, la `break` instruction termine la boucle après 14 nombres.  
  
```JavaScript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 Dans le code suivant, le `break` instruction fait référence à la `for` boucle est précédé par le `Inner:` instruction. Lorsque `j` est égal à 24, le `break` instruction provoque le flux du programme à quitter cette boucle. Les nombres 21 à 23 s’impriment sur chaque ligne.  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [continue, instruction](../../javascript/reference/continue-statement-javascript.md)   
 [Instruction Do... while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Instruction for](../../javascript/reference/for-statement-javascript.md)   
 [instruction for... dans l’instruction](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instruction étiquetée](../../javascript/reference/labeled-statement-javascript.md)   
 [Instruction while](../../javascript/reference/while-statement-javascript.md)