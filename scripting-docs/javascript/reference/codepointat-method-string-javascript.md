---
title: "codepointat, méthode (String) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dd5ef17db177dfb1d532bfb88d1d0d77cdb7304
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="codepointat-method-string-javascript"></a>codePointAt, méthode (String) (JavaScript)
Retourne le point de code d'un caractère Unicode UTF-16.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `stringObj`  
 Obligatoire. Objet string.  
  
 `pos`  
 Obligatoire. Position du caractère.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode retourne les valeurs de point de code, y compris les points de code astral (points de code avec plus de quatre valeurs hexadécimales), pour tous les caractères UTF-16.  
  
 Si `pos` est inférieur à zéro (0) ou supérieur à la taille de la chaîne, la valeur de retour est `undefined`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `codePointAt`.  
  
```JavaScript  
var cp1 = "𠮷".codePointAt(0);  
var cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98   
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
