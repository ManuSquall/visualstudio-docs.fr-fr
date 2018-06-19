---
title: If... else, instruction (JavaScript) | Documents Microsoft
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
- else_JavaScriptKeyword
- if_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- if statement, if...else
- loop structures, if...else statements
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fad12b970f69a15040acb59195f957a2a6eec3e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637329"
---
# <a name="ifelse-statement-javascript"></a>if...else, instruction (JavaScript)
Exécute un groupe d'instructions soumises à une condition, en fonction de la valeur d'une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## <a name="parameters"></a>Paramètres  
 `condition1`  
 Obligatoire. Expression booléenne. Si `condition1` est `null` ou `undefined`, `condition1` est traité comme `false`.  
  
 `statement1`  
 Facultatif. L’instruction à exécuter si `condition1` est **true**. Il peut s'agir d'une instruction composée.  
  
 `condition2`  
 Condition à évaluer.  
  
 `statement2`  
 Facultatif. L’instruction à exécuter si `condition2` est `true`. Il peut s'agir d'une instruction composée.  
  
 `statement3`  
 Si les deux `condition1` et `condition2` sont `false`, cette instruction est exécutée.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser `if`, `if else`, et `else`.  
  
 Il est conseillé de placer `statement1` et `statement2` entre accolades ({}) par souci de clarté et éviter les erreurs.  
  
```JavaScript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [?: (conditionnel ternaire), opérateur](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)