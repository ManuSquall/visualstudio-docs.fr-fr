---
title: Do... while, instruction (JavaScript) | Documents Microsoft
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
- do_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- terminating loops
- loop structures, do and do-while
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 895d98a3de3a6691ce60bf0456bb838403619f88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636629"
---
# <a name="dowhile-statement-javascript"></a>do...while, instruction (JavaScript)
Exécute un bloc d’instructions une fois, puis répète l’exécution de la boucle jusqu'à ce qu’une expression de condition prend la valeur `false`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## <a name="parameters"></a>Paramètres  
 `statement`  
 Obligatoire. L’instruction à exécuter si `expression` est `true`. Il peut s'agir d'une instruction composée.  
  
 `expression`  
 Obligatoire. Une expression peut être convertie en valeur booléenne `true` ou `false`. Si `expression` est `true`, la boucle est exécutée à nouveau. Si `expression` est `false`, la boucle se termine.  
  
## <a name="remarks"></a>Remarques  
 Contrairement à la `while` instruction, un `do...while` boucle est exécutée une fois avant l’évaluation de l’expression conditionnelle.  
  
 Sur n’importe quelle ligne dans un `do...while` bloc, vous pouvez utiliser la `break` instruction pour forcer le flux de programme quitter la boucle, ou vous pouvez utiliser la `continue` instruction accéder directement à la `while` expression.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, les instructions figurant dans le `do...while` boucle continuent de s’exécuter tant que la variable `i` est inférieure à 10.  
  
```JavaScript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, les instructions à l’intérieur de la boucle sont exécutées une fois même si la condition n’est pas remplie.  
  
```JavaScript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [break, instruction](../../javascript/reference/break-statement-javascript.md)   
 [continue, instruction](../../javascript/reference/continue-statement-javascript.md)   
 [Instruction for](../../javascript/reference/for-statement-javascript.md)   
 [instruction for... dans l’instruction](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while, instruction](../../javascript/reference/while-statement-javascript.md)   
 [Instruction étiquetée](../../javascript/reference/labeled-statement-javascript.md)