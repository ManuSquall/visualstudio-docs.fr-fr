---
title: var, instruction (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- var_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, var statement
- var statement
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839b6904fa59b6f4ea9a5c4d8e00213cd351517a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641359"
---
# <a name="var-statement-javascript"></a>var, instruction (JavaScript)
Déclare une variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
var variable1 = value1  
```  
  
## <a name="parameters"></a>Paramètres  
 `variable1`  
 Le nom de la variable déclarée.  
  
 `value1`  
 La valeur initiale assignée à la variable.  
  
## <a name="remarks"></a>Remarques  
 Utilisez la `var` instruction pour déclarer des variables. Vous pouvez assigner des valeurs aux variables lorsque vous les déclarez ou plus loin dans votre script.  
  
 Une variable est déclarée à la première fois qu’il apparaît dans votre script.  
  
 Vous pouvez déclarer une variable sans utiliser le `var` (mot clé) et affecter une valeur à celle-ci. Il s’agit comme un *déclaration implicite*, et il n’est pas recommandé. Une déclaration implicite donne la portée des variables globale. Lorsque vous déclarez une variable au niveau de la procédure, cependant, en général, non voulues à ont une portée globale. Pour éviter d’accorder la portée des variables globale, vous devez utiliser le `var` mot clé dans votre déclaration de variable.  
  
 Si vous n’initialisez pas votre variable dans la `var` instruction, il est automatiquement attribué la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valeur `undefined`.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants illustrent l’utilisation de la `var` instruction.  
  
```JavaScript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction Function](../../javascript/reference/function-statement-javascript.md)   
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Variables](../../javascript/variables-javascript.md)