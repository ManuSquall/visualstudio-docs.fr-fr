---
title: const, instruction (JavaScript) | Documents Microsoft
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
- const_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, const statement
- const statement
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68130cec4f1b1fe89d2fe3e673b28963d79aebde
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634099"
---
# <a name="const-statement-javascript"></a>const, instruction (JavaScript)
Déclare une variable de portée de bloc avec une valeur de constante.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
const constant1 = value1  
```  
  
#### <a name="parameters"></a>Paramètres  
 `constant1`  
 Le nom de la variable déclarée.  
  
 `value1`  
 La valeur initiale assignée à la variable.  
  
## <a name="remarks"></a>Remarques  
 Utilisez la `const` instruction pour déclarer une variable avec une valeur constante, dont la portée est limitée au bloc dans lequel elle est déclarée. La valeur de la variable ne peut pas être modifiée.  
  
 Une variable déclarée à l’aide de `const` doit être initialisée lorsqu’elle est déclarée.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de l'instruction `const`.  
  
```JavaScript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Let (instruction)](../../javascript/reference/let-statement-javascript.md)   
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Objet Array](../../javascript/reference/array-object-javascript.md)   
 [Variables](../../javascript/variables-javascript.md)