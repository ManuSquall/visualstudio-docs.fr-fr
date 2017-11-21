---
title: "Reverse (méthode) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: reverse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], reversing elements
- reverse method
- transposing elements
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a34385ccf89557688698b50384b3dfe359478df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="reverse-method-javascript"></a>reverse, méthode (JavaScript)
Inverse les éléments dans un `Array`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
arrayObj.reverse()   
```  
  
## <a name="parameters"></a>Paramètres  
 `arrayObj`  
 Obligatoire. Tout objet `Array`.  
  
## <a name="return-value"></a>Valeur de retour  
 Le tableau inversé.  
  
## <a name="remarks"></a>Remarques  
 Requis `arrayObj` référence est un `Array` objet.  
  
 Le `reverse` méthode inverse les éléments d’un `Array` objet sur place. Il ne crée pas un nouveau `Array` objet pendant l’exécution.  
  
 Si le tableau n’est pas contigu, la `reverse` méthode crée des éléments dans le tableau qui combler les vides dans le tableau. Chacun de ces éléments a la valeur `undefined`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `reverse`.  
  
```JavaScript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode concat (tableau)](../../javascript/reference/concat-method-array-javascript.md)