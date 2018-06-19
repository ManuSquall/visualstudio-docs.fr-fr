---
title: callee, propriété (arguments) (JavaScript) | Documents Microsoft
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
- callee
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- callee property
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33f1c2926d76c0a1f088c8f4222b6f24c004b73b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634059"
---
# <a name="callee-property-arguments-javascript"></a>callee, propriété (arguments) (JavaScript)
Retourne le `Function` objet en cours d’exécution, autrement dit, le corps du texte de l’objet `Function` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[function.]arguments.callee  
```  
  
## <a name="remarks"></a>Remarques  
 Le paramètre facultatif *fonction* argument est le nom d’en cours d’exécution `Function` objet.  
  
 Le `callee` propriété est un membre de la **arguments** objet qui est disponible uniquement lorsque la fonction associée est l’exécution.  
  
 La valeur initiale de la `callee` propriété est le `Function` de l’objet en cours d’exécution. Cela permet aux fonctions anonymes d’être récursives.  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S’applique à**: [objet arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Objet de fonction](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété caller (Function)](../../javascript/reference/caller-property-function-javascript.md)