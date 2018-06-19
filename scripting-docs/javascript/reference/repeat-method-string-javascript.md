---
title: Méthode Repeat (String) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1a3d6edce877a97b0e46a69c43b667231c26981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638709"
---
# <a name="repeat-method-string-javascript"></a>repeat, méthode (String) (JavaScript)
Retourne un nouvel objet String avec une valeur égale à la chaîne d'origine répétée le nombre de fois spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
stringObj.repeat(count);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `stringObj`  
 Obligatoire. Objet string.  
  
 `count`  
 Obligatoire. Nombre de répétitions de la chaîne d'origine dans la chaîne retournée.  
  
## <a name="exceptions"></a>Exceptions  
 Cette méthode génère une erreur RangeError si et seulement si l’argument est négatif ou +Infini.  
  
## <a name="remarks"></a>Remarques  
 La méthode `repeat` concatène la chaîne d'origine dans la nouvelle chaîne le nombre de fois spécifié par `count`.  
  
 Cette méthode génère une erreur si `count` n'est pas un nombre positif inférieur à `Infinity`.  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]