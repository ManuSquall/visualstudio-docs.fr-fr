---
title: "Opérateur conditionnel (ternaire) ( ? :)) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '?:'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional operators
- conditional (Ternary) operator
- ternary
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dc34b5c633cfc02219cb01061e1aaa017e0f7f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-ternary-operator--javascript"></a>conditionnel, opérateur (ternaire) (?:) (JavaScript)
En fonction d'une condition, retourne l'une ou l'autre des deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
test ? expression1 : expression2  
```  
  
## <a name="parameters"></a>Paramètres  
 `test`  
 Toute expression booléenne.  
  
 `expression1`  
 Une expression retournée si `test` a la valeur `true`. Il peut s'agir d'une expression avec virgules.  
  
 `expression2`  
 Une expression retournée si `test` a la valeur `false`. Plusieurs expressions peuvent être liées par une expression avec virgules.  
  
## <a name="remarks"></a>Remarques  
 L'opérateur `?:` peut être utilisé comme raccourci pour une instruction `if...else`. Il est généralement employé dans une expression plus longue où une instruction `if...else` ne serait pas appropriée. Exemple :  
  
```JavaScript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 L’exemple crée une chaîne contenant « Good evening. » Si elle est exécutée après 18 heures. Le code équivalent avec l'instruction `if...else` se présenterait comme ceci :  
  
```JavaScript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [If... else, instruction](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [Script Junkie configuration widget exemple d’application](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)