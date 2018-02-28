---
title: "setUTCMilliseconds, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- setUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- dates, UTC
- UTC times, setting
- setUTCMilliseconds method
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279d00b256b3b0763e2f15f549fdc6ee81c20254
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="setutcmilliseconds-method-date-javascript"></a>setUTCMilliseconds, méthode (Date) (JavaScript)
Définit la valeur en millisecondes le `Date` de l’objet à l’aide de temps universel coordonné (UTC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 `numMilli`  
 Obligatoire. Valeur numérique égale à la valeur en millisecondes.  
  
## <a name="remarks"></a>Remarques  
 Pour définir les millisecondes en heure locale, utilisez la `setMilliseconds` (méthode).  
  
 Si la valeur de `numMilli` est supérieur à 999, ou est un nombre négatif, le stockés un certain nombre de secondes (minutes, heures et ainsi de suite, si nécessaire) est incrémenté une quantité appropriée.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setUTCMilliseconds`.  
  
```JavaScript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getMilliseconds, méthode (Date)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds, méthode (Date)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [Méthode setMilliseconds (Date)](../../javascript/reference/setmilliseconds-method-date-javascript.md)