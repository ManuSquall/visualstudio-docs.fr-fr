---
title: charAt, méthode (String) (JavaScript) | Documents Microsoft
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
- charAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object, returning characters
- charAt method
- characters, returning part of
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 201d85fec4ba184f0842c7401d986650b9ee078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634129"
---
# <a name="charat-method-string-javascript"></a>charAt, méthode (String) (JavaScript)
Retourne le caractère situé à l'index spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
strObj. charAt(index)  
```  
  
## <a name="parameters"></a>Paramètres  
 `strObj`  
 Obligatoire. N’importe quel `String` objet ou un littéral de chaîne.  
  
 `index`  
 Obligatoire. Index de base zéro du caractère souhaité.  
  
## <a name="remarks"></a>Remarques  
 Le `charAt` méthode retourne une valeur de caractère égale au caractère à la position spécifiée `index`. Le premier caractère dans une chaîne est à l’index 0, le deuxième à l’index 1 et ainsi de suite. Les valeurs de `index` qui sont hors limites retour d’une chaîne vide.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `charAt` méthode :  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objet String](../../javascript/reference/string-object-javascript.md)