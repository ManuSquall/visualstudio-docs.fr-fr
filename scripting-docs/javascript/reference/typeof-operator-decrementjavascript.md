---
title: typeof, opérateur (JavaScript) | Documents Microsoft
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
- typeof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- typeof operator
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9ff8c7942c773d138dd599956c41d1e583e6288
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
ms.locfileid: "29899628"
---
# <a name="typeof-operator-javascript"></a>typeof, opérateur (JavaScript)
Retourne une chaîne qui identifie le type de données d'une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## <a name="remarks"></a>Notes  
 Le *expression* argument peut être toute expression de type pour lequel les informations sont recherchées.  
  
 Le `typeof` opérateur retourne des informations de type sous forme de chaîne. Il existe sept différentes valeurs `typeof` retourne : « number », « chaîne » « boolean », « objet » « fonction, », « non définie » et « inconnu ».  
  
 Les parenthèses sont facultatives dans le `typeof` syntaxe.  

 Un objet peut retourner comme un type inconnu dans une requête XMLHTTPRequest. Un objet COM avec aucune analogique en JavaScript peut-être également renvoyer un type inconnu.
  
## <a name="example"></a>Exemple  
 L’exemple suivant teste le type de données de variables.  
  
```JavaScript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant teste un type de données de `undefined` pour les variables déclarées et non déclarés.  
  
```JavaScript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## <a name="requirements"></a>Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getPrototypeOf Function](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [Constante undefined](../../javascript/reference/undefined-constant-javascript.md)   
 [Opérateurs de comparaison](../../javascript/reference/comparison-operators-javascript.md)   
 [Types de données](../../javascript/data-types-javascript.md)   
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)