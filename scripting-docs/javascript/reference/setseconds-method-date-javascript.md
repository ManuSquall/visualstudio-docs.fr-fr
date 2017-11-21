---
title: "setSeconds, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setSeconds method
- seconds method
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b8d545307f6aac3506310c868a2860a6159a106
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="setseconds-method-date-javascript"></a>setSeconds, méthode (Date) (JavaScript)
Affecte la valeur secondes le `Date` en heure locale de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 *numSeconds n'*  
 Obligatoire. Valeur numérique égale à la valeur des secondes.  
  
 `numMilli`  
 Facultatif. Valeur numérique égale à la valeur en millisecondes.  
  
## <a name="remarks"></a>Remarques  
 Tous les **définir** méthodes acceptant des arguments facultatifs utilisent la valeur retournée par correspondant **obtenir** méthodes, si vous ne spécifiez pas un argument facultatif. Par exemple, si le `numMilli` argument n’est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par la **getMilliseconds** (méthode).  
  
 Pour définir les secondes en temps universel coordonné (UTC), utilisez le `setUTCSeconds` (méthode).  
  
 Si la valeur d’un argument est supérieure à sa plage ou est un nombre négatif, les autres valeurs stockées sont modifiées en conséquence. Par exemple, si la date stockée est « Jan 5, 1996 00:00:00 » et **setSeconds(150)** est appelée, la date est modifiée en « le 5 janvier 1996 00:02:30. »  
  
 Le `setHours` méthode peut être utilisée pour définir les heures, minutes, secondes et les millisecondes.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setSeconds`.  
  
```JavaScript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getSeconds, méthode (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds, méthode (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Méthode setUTCSeconds (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)