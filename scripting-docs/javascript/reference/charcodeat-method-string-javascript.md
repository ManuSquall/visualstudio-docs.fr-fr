---
title: charCodeAt, méthode (String) (JavaScript) | Documents Microsoft
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
- charCodeAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- charCodeAt method
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e7b8e62dfd29aa42d9816d0c5e27cc90440751a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633949"
---
# <a name="charcodeat-method-string-javascript"></a>charCodeAt, méthode (String) (JavaScript)
Retourne la valeur Unicode du caractère situé à l’emplacement spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## <a name="parameters"></a>Paramètres  
 `strObj`  
 Obligatoire. N’importe quel `String` objet ou un littéral de chaîne.  
  
 `index`  
 Obligatoire. Index de base zéro du caractère souhaité. S’il n’existe aucun caractère à l’index spécifié, `NaN` est retourné.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `charCodeAt`.  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)