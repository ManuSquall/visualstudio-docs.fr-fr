---
title: setUTCSeconds, méthode (Date) (JavaScript) | Documents Microsoft
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
- setUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCSeconds method
- UTC times, setting
- seconds method
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3df010cd84332d8957f1c08c41c4543dec36e4a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640539"
---
# <a name="setutcseconds-method-date-javascript"></a>setUTCSeconds, méthode (Date) (JavaScript)
Affecte la valeur secondes le `Date` de l’objet à l’aide de temps universel coordonné (UTC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 *numSeconds n'*  
 Obligatoire. Valeur numérique égale à la valeur des secondes.  
  
 `numMilli`  
 Facultatif. Valeur numérique égale à la valeur en millisecondes.  
  
## <a name="remarks"></a>Remarques  
 Tous les **définir** méthodes acceptant des arguments facultatifs utilisent la valeur retournée par correspondant **obtenir** méthodes, si vous ne spécifiez pas un argument facultatif. Par exemple, si le `numMilli` argument n’est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par le `getUTCMilliseconds` (méthode).  
  
 Pour définir les secondes en heure locale, utilisez la `setSeconds` (méthode).  
  
 Si la valeur d’un argument est supérieure à sa plage ou est un nombre négatif, les autres valeurs stockées sont modifiées en conséquence. Par exemple, si la date stockée est « 5 Jan 1996 00:00:00.00 » et **setSeconds(150)** est appelée, la date est remplacée par « 5 Jan 1996 00:02:30.00. »  
  
 Le **setUTCHours** méthode peut être utilisée pour définir les heures, minutes, secondes et les millisecondes.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setUTCSeconds`.  
  
```JavaScript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getSeconds, méthode (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds, méthode (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Méthode setSeconds (Date)](../../javascript/reference/setseconds-method-date-javascript.md)