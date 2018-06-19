---
title: Propriété Length (fonction) (JavaScript) | Documents Microsoft
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
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Length property
- length property (function)
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fbd0334c18da2c6ef8de8366555d79f791e6855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637829"
---
# <a name="length-property-function-javascript"></a>length, propriété (Function) (JavaScript)
Obtient le nombre d’arguments définis pour une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
functionName.length  
```  
  
## <a name="remarks"></a>Remarques  
 Requis *functionName* est le nom de la fonction.  
  
 Le **longueur** propriété d’une fonction est initialisée par le moteur de script pour le nombre d’arguments dans la définition de la fonction lorsqu’une instance de la fonction est créée.  
  
 Que se passe-t-il quand une fonction est appelée avec un nombre d’arguments différentes de celle de son **longueur** propriété dépend de la fonction.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **longueur** propriété :  
  
```JavaScript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [arguments, propriété (fonction)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Length, propriété (Array)](../../javascript/reference/length-property-array-javascript.md)   
 [Propriété length (Chaîne)](../../javascript/reference/length-property-string-javascript.md)