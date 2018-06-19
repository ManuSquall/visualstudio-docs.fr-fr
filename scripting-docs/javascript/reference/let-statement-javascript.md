---
title: Let, instruction (JavaScript) | Documents Microsoft
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
- let_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- let statement
- declaring variables, let statement
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c447a1bf0c430771ff146965a592f7e160e2055b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638889"
---
# <a name="let-statement-javascript"></a>let, instruction (JavaScript)
Déclare une variable de portée de bloc  
  
## <a name="syntax"></a>Syntaxe  
  
```  
let variable1 = value1  
```  
  
#### <a name="parameters"></a>Paramètres  
 `variable1`  
 Le nom de la variable déclarée.  
  
 `value1`  
 La valeur initiale assignée à la variable.  
  
## <a name="remarks"></a>Remarques  
 Utilisez la `let` instruction pour déclarer une variable dont la portée est limitée au bloc dans lequel elle est déclarée. Vous pouvez assigner des valeurs aux variables lorsque vous les déclarez ou plus loin dans votre script.  
  
 Une variable déclarée à l’aide de `let` ne peut pas être utilisée avant sa déclaration ou une erreur provoque.  
  
 Si vous n’initialisez pas votre variable dans la `let` instruction, il est automatiquement attribué la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valeur `undefined`.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de l'instruction `let`.  
  
```JavaScript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [const (instruction)](../../javascript/reference/const-statement-javascript.md)   
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Variables](../../javascript/variables-javascript.md)