---
title: Function, instruction (JavaScript) | Documents Microsoft
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
- function_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator
- declaring functions, syntax
- function statement
- declaring functions
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5fac3647e9374a9c909a420b73b86354cac69b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="function-statement-javascript"></a>function, instruction (JavaScript)
Déclare une nouvelle fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Paramètres  
 `functionname`  
 Obligatoire. Nom de la fonction.  
  
 `arg1...argN`  
 Facultatif. Liste facultative d’arguments séparés par des virgules que comprend la fonction.  
  
 `statements`  
 Facultatif. Un ou plusieurs[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] instructions.  
  
## <a name="remarks"></a>Remarques  
 Utilisez la `function` instruction pour déclarer une fonction pour une utilisation ultérieure. Le code qui est contenu dans `statements` n’est pas exécuté jusqu'à ce que la fonction est appelée depuis un autre emplacement dans le script.  
  
 Le [retourner](../../javascript/reference/return-statement-javascript.md) instruction est utilisée pour retourner une valeur de la fonction. Vous n’avez pas à utiliser un `return` instruction ; la programme sera retourner lorsqu’il atteint la fin de la fonction. Si aucun `return` instruction est exécutée dans la fonction, ou si le `return` instruction ne possède aucune expression, la fonction retourne la valeur `undefined`.  
  
> [!NOTE]
>  Lorsque vous appelez une fonction, veillez à inclure les parenthèses et tous les arguments requis. Appel d’une fonction sans parenthèses retourne une référence à la fonction, pas les résultats de la fonction.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de l'instruction `function`.  
  
```JavaScript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## <a name="example"></a>Exemple  
 Une fonction peut être assignée à une variable. L'exemple suivant illustre cette opération.  
  
```JavaScript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)