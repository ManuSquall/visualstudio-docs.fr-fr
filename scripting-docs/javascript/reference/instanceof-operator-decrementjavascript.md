---
title: instanceof, opérateur (JavaScript) | Documents Microsoft
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
- instanceof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- instanceOf operator
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2124fe815c89c3c157be3ea729fa7edb9d96b39
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
ms.locfileid: "27799579"
---
# <a name="instanceof-operator-javascript"></a>instanceof, opérateur (JavaScript)
Retourne une valeur booléenne indiquant si un objet est une instance d'une classe particulière.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = object instanceof class  
```  
  
## <a name="parameters"></a>Paramètres  
 `result`  
 Obligatoire. Toute variable.  
  
 `object`  
 Obligatoire. Toute expression d'objet.  
  
 `class`  
 Obligatoire. Toute classe d'objets définie.  
  
## <a name="remarks"></a>Notes  
 L'opérateur `instanceof` retourne la valeur `true` si `object` est une instance de `class`. Elle retourne `true` si `class` est présent dans la chaîne de prototype de l’objet. Il retourne la valeur `false` si `object` n'est pas une instance de `class`, ou si `object` a la valeur `null`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de l'opérateur `instanceof`.  
  
```JavaScript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## <a name="requirements"></a>Configuration requise  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)