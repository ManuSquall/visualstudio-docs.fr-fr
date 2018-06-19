---
title: 0... n, propriétés (arguments) (JavaScript) | Documents Microsoft
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
- 0...n
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- 0...n properties
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f46c7dafef1cdc27d27f619936349637af172740
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634009"
---
# <a name="0n-properties-arguments-javascript"></a>0...n, propriétés (arguments) (JavaScript)
Retourne la valeur réelle des arguments individuels d’un **arguments** objet retourné par la **arguments** propriété d’une fonction en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## <a name="parameters"></a>Paramètres  
 *function*  
 Facultatif. Le nom d’en cours d’exécution `Function` objet.  
  
 0, 1, 2, *, n*  
 Obligatoire. Entier non négatif dans la plage de 0 à  *n*  où 0 représente le premier argument et  *n*  représente l’argument final. La valeur de l’argument final  *n*  est **.Length-1**.  
  
## <a name="remarks"></a>Remarques  
 Les valeurs retournées par la valeur 0. . . n sont les valeurs réelles passés à la fonction en cours d’exécution. Lors de la non réellement un tableau d’arguments, les arguments individuels qui composent le **arguments** objet sont accessibles de la même façon que les éléments du tableau sont accessibles.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **0...**  ***n***propriétés de la **arguments** objet. Pour bien comprendre l’exemple, passer un ou plusieurs arguments à la fonction :  
  
```JavaScript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S’applique à**: [objet arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Objet de fonction](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Length, propriété (arguments)](../../javascript/reference/length-property-arguments-javascript.md)   
 [Propriété length (Fonction)](../../javascript/reference/length-property-function-javascript.md)