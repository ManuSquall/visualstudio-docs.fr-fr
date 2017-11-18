---
title: "arguments, propriété (fonction) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments property
- Arguments property
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0b18fb8164639119e5db5e7a5d76b4280f9c9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-property-function-javascript"></a>arguments, propriété (Function) (JavaScript)
Obtient les arguments d’en cours d’exécution `Function` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
function.arguments  
```  
  
## <a name="remarks"></a>Remarques  
 Le `function` argument est le nom de la fonction en cours d’exécution et peut être omis.  
  
 Cette propriété permet à une fonction gérer un nombre variable d’arguments. Le **longueur** propriété de la `arguments` objet contient le nombre d’arguments passés à la fonction. Les arguments individuels contenus dans le `arguments` objet sont accessibles de la même façon que les éléments de tableau.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de la propriété `arguments` :  
  
```JavaScript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Objet arguments](../../javascript/reference/arguments-object-javascript.md)   
 [Instruction function](../../javascript/reference/function-statement-javascript.md)