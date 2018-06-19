---
title: Call, méthode (Function) (JavaScript) | Documents Microsoft
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
- call
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- call method
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ef871f85459ad875a747ae79c7c054b30a82e55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634109"
---
# <a name="call-method-function-javascript"></a>call, méthode (Function) (JavaScript)
Appelle une méthode d’un objet, en remplaçant un autre objet pour l’objet actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## <a name="parameters"></a>Paramètres  
 `thisObj`  
 Facultatif. Objet à utiliser en tant que l’objet actuel.  
  
 `arg1, arg2, , argN`  
 Facultatif. Une liste d’arguments à passer à la méthode.  
  
## <a name="remarks"></a>Remarques  
 Le `call` méthode est utilisée pour appeler une méthode pour le compte d’un autre objet. Il vous permet de modifier le `this` objet d’une fonction à partir du contexte d’origine au nouvel objet spécifié par `thisObj`.  
  
 Si `thisObj` n’est pas fourni, le `global` objet est utilisé en tant que `thisObj`.  
  
## <a name="example"></a>Exemple  
 Le code suivant met en œuvre la méthode `call`.  
  
```JavaScript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de fonction](../../javascript/reference/function-object-javascript.md)   
 [Méthode apply (Function)](../../javascript/reference/apply-method-function-javascript.md)