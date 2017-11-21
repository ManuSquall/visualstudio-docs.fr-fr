---
title: "setUTCHours, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- UTC times, setting
- setUTCHours method
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fe83735028f86d38ef270beac6c44dfa4caae7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="setutchours-method-date-javascript"></a>setUTCHours, méthode (Date) (JavaScript)
Définit la valeur des heures le `Date` de l’objet à l’aide de temps universel coordonné (UTC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 `numHours`  
 Obligatoire. Valeur numérique égale à la valeur en heures.  
  
 `numMin`  
 Facultatif. Valeur numérique égale à la valeur des minutes. Doit être fourni si le paramètre `numSec` ou `numMilli` sont utilisés.  
  
 `numSec`  
 Facultatif. Valeur numérique égale à la valeur des secondes. Doit être fournie si `numMilli` argument est utilisé.  
  
 `numMilli`  
 Facultatif. Valeur numérique égale à la valeur en millisecondes.  
  
## <a name="remarks"></a>Remarques  
 Tous les **définir** méthodes acceptant des arguments facultatifs utilisent la valeur retournée par correspondant **obtenir** méthodes, si vous ne spécifiez pas un argument facultatif. Par exemple, si le `numMin` argument n’est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par le `getUTCMinutes` (méthode).  
  
 Pour définir la valeur des heures en heure locale, utilisez la `setHours` (méthode).  
  
 Si la valeur d’un argument est supérieure à la plage, ou est un nombre négatif, les autres valeurs stockées sont modifiées en conséquence. Par exemple, si la date stockée est « 5 Jan 1996 00:00:00.00 », et **setUTCHours(30)** est appelée, la date est modifiée en « 6 Jan 1996 06:00:00.00. »  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setUTCHours`.  
  
```JavaScript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getHours, méthode (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours, méthode (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Méthode setHours (Date)](../../javascript/reference/sethours-method-date-javascript.md)