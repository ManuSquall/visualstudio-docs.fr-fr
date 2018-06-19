---
title: while, instruction (JavaScript) | Documents Microsoft
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
- while_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, while statements
- while statement
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de64bf9181a0fc86a528fa7af21216b99530f217
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641249"
---
# <a name="while-statement-javascript"></a>while, instruction (JavaScript)
Exécute une instruction ou une série d’instructions jusqu'à ce qu’une condition spécifiée est `false`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
while (expression) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Paramètres  
 `expression`  
 Obligatoire. Une expression booléenne est vérifiée avant chaque itération de la boucle. Si `expression` est `true`, la boucle est exécutée. Si `expression` est `false`, la boucle se termine.  
  
 `statements`  
 Facultatif. Une ou plusieurs instructions à exécuter si `expression` est `true`.  
  
## <a name="remarks"></a>Remarques  
 Le `while` instruction vérifications `expression` avant la première fois une boucle. Si `expression` est `false` à ce stade, la boucle n’est jamais exécutée.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de l'instruction `while`.  
  
```JavaScript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [break, instruction](../../javascript/reference/break-statement-javascript.md)   
 [continue, instruction](../../javascript/reference/continue-statement-javascript.md)   
 [Instruction Do... while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Instruction for](../../javascript/reference/for-statement-javascript.md)   
 [Instruction for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)