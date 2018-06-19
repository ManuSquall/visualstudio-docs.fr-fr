---
title: caller, propriété (fonction) (JavaScript) | Documents Microsoft
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
- caller
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- caller property
- function calls, functions that are executing
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c6eef1b8304612c2ed16a4cc389bf3b2a28b70f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634139"
---
# <a name="caller-property-function-javascript"></a>caller, propriété (Function) (JavaScript)
Obtient la fonction qui a appelé la fonction actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
functionName.caller  
```  
  
## <a name="remarks"></a>Remarques  
 Le `functionName` est le nom de n’importe quel l’exécution de fonction de l’objet.  
  
 Le `caller` propriété est définie pour une fonction uniquement lors de l’exécution de fonction. Si la fonction est appelée à partir du haut niveau d’un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] programme, `caller` contient `null`.  
  
 Si le `caller` propriété est utilisée dans un contexte de chaîne, le résultat est le même que `functionName`.`toString`, autrement dit, le texte décompilé de la fonction s’affiche.  
  
 L'exemple ci-dessous illustre l'utilisation de la propriété `caller` :  
  
```JavaScript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction function](../../javascript/reference/function-statement-javascript.md)