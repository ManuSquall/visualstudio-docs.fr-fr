---
title: setHours, méthode (Date) (JavaScript) | Documents Microsoft
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
- setHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- setHours method
- dates, setting
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9757f8416953eaf756dba96b91100527606cf9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640959"
---
# <a name="sethours-method-date-javascript"></a>setHours, méthode (Date) (JavaScript)
Définit la valeur d’heure le `Date` en heure locale de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 `numHours`  
 Obligatoire. Valeur numérique égale à la valeur en heures.  
  
 `numMin`  
 Facultatif. Valeur numérique égale à la valeur des minutes. Doit être fourni si un des arguments suivants est utilisé.  
  
 `numSec`  
 Facultatif. Valeur numérique égale à la valeur des secondes. Doit être fournie si l’argument suivant est utilisé.  
  
 `numMilli`  
 Facultatif. Valeur numérique égale à la valeur en millisecondes.  
  
## <a name="remarks"></a>Remarques  
 Tous les **définir** méthodes acceptant des arguments facultatifs utilisent la valeur retournée par correspondant **obtenir** méthodes, si vous ne spécifiez pas un argument facultatif. Par exemple, si le `numMinutes` argument n’est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par le `getMinutes` (méthode).  
  
 Pour définir la valeur des heures à l’aide de temps universel coordonné (UTC), utilisez le `setUTCHours` (méthode).  
  
 Si la valeur d’un argument est supérieure à sa plage ou est un nombre négatif, les autres valeurs stockées sont modifiées en conséquence. Par exemple, si la date stockée est « Jan 5, 1996 00:00:00 », et **setHours(30)** est appelée, la date est modifiée en « Jan 6, 1996 06:00:00. » Les nombres négatifs ont un comportement similaire.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setHours`.  
  
```JavaScript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getHours, méthode (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours, méthode (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Méthode setUTCHours (Date)](../../javascript/reference/setutchours-method-date-javascript.md)