---
title: return, instruction (JavaScript) | Documents Microsoft
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
- return_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- terminating execution
- return statement
- function statement
- return statement, syntax
- return statement, exiting functions in script
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c28f17bed2dfff021ea1aea268bb7a2eb3f3e58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639329"
---
# <a name="return-statement-javascript"></a>return, instruction (JavaScript)
Quitte la fonction en cours et retourne une valeur de cette fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
return[(][expression][)];   
```  
  
## <a name="remarks"></a>Remarques  
 Le paramètre facultatif *expression* argument est la valeur à retourner à partir de la fonction. Si omis, la fonction ne retourne pas de valeur.  
  
 Vous utilisez la `return` instruction pour arrêter l’exécution d’une fonction et retourner la valeur de *expression*. Si *expression* est omis, ou aucun `return` instruction est exécutée à partir de la fonction, l’expression qui a appelé la fonction en cours est affectée à la valeur undefined.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de l'instruction `return`.  
  
```JavaScript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `return` instruction pour retourner une fonction.  
  
```JavaScript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction function](../../javascript/reference/function-statement-javascript.md)