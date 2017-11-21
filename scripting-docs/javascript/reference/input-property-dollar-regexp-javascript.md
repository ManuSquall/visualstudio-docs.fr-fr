---
title: "Propriété Input ($_) (RegExp) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: $_
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- input property
- $_ property
ms.assetid: 88c6d1d8-56f7-4334-a7eb-e899aec9cda4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a447950783473d975bfe799eaa2bf18008e539e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="input-property--regexp-javascript"></a>input, propriété ($_) (RegExp) (JavaScript)
Retourne la chaîne sur laquelle une recherche d’expression régulière a été effectuée. Lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RegExp.input  
```  
  
## <a name="remarks"></a>Remarques  
 L’objet associé à cette propriété est toujours global `RegExp` objet.  
  
 La valeur de **d’entrée** propriété est modifiée à tout moment la chaîne recherchée est modifiée.  
  
 L’exemple suivant illustre l’utilisation de la **d’entrée** propriété :  
  
```JavaScript  
function inputDemo(){  
   var s;  
   var re = new RegExp("d(b+)(d)","ig");  
   var str = "cdbBdbsbdbdz";  
   var arr = re.exec(str);  
   s = "The string used for the match was " + RegExp.input;   
   return(s);  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [RegExp (objet)](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)