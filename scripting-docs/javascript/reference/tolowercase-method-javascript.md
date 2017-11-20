---
title: "toLowerCase (méthode) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLowerCase method
ms.assetid: dfd543b9-3e7a-4f83-a391-9cde109ad6bc
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7510e074c11cf3d3f63b965bcd6f14946dc5a16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="tolowercase-method-javascript"></a>toLowerCase, méthode (JavaScript)
Convertit tous les caractères alphabétiques dans une chaîne en minuscules.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      strVariable.toLowerCase()  
"String Literal".toLowerCase()   
```  
  
## <a name="remarks"></a>Remarques  
 Le `toLowerCase` méthode n’a aucun effet sur les caractères non alphabétiques.  
  
 L’exemple suivant montre les effets de la `toLowerCase` méthode :  
  
```JavaScript  
var str1 = "This is a STRING.";  
var str2 = str1. toLowerCase();  
document.write(str2);  
  
// Output: this is a string.  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [toLocaleLowerCase, méthode (String)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [Méthode toUpperCase (String)](../../javascript/reference/touppercase-method-string-javascript.md)