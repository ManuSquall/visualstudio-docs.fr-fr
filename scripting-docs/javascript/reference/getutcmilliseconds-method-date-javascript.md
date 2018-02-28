---
title: "getUTCMilliseconds, méthode (Date) (JavaScript) | Documents Microsoft"
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
- getUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- UTC times, returning
- getUTCMilliseconds method
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fb7cf202c8511bec00c10dc5b8c23bd198d8700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="getutcmilliseconds-method-date-javascript"></a>getUTCMilliseconds, méthode (Date) (JavaScript)
Obtient les millisecondes d’un `Date` à l’aide de temps universel coordonné (UTC) de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de millisecondes qui peut être comprises entre 0 et 999.  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir le nombre de millisecondes en heure locale, utilisez la `getMilliseconds` (méthode).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getUTCMilliseconds`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getMilliseconds, méthode (Date)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [setMilliseconds, méthode (Date)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [Méthode setUTCMilliseconds (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)