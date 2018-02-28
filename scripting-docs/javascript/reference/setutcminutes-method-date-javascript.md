---
title: "setUTCMinutes, méthode (Date) (JavaScript) | Documents Microsoft"
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
- setUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- dates, UTC
- UTC times, setting
- setUTCMinutes method
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37df1bcefa358f2c9076a3da877bd642d19178b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="setutcminutes-method-date-javascript"></a>setUTCMinutes, méthode (Date) (JavaScript)
Définit la valeur des minutes le `Date` de l’objet à l’aide de temps universel coordonné (UTC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 `numMinutes`  
 Obligatoire. Valeur numérique égale à la valeur des minutes. Doit être fourni si un des arguments suivants est utilisé.  
  
 *numSeconds n'*  
 Facultatif. Valeur numérique égale à la valeur des secondes. Doit être fournie si `numMilli` est utilisé.  
  
 `numMilli`  
 Facultatif. Valeur numérique égale à la valeur en millisecondes.  
  
## <a name="remarks"></a>Remarques  
 Tous les **définir** méthodes acceptant des arguments facultatifs utilisent la valeur retournée par correspondant **obtenir** méthodes, si vous ne spécifiez pas un argument facultatif. Par exemple, si le *numSeconds ne* argument n’est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par le `getUTCSeconds` (méthode).  
  
 Pour modifier la valeur des minutes en heure locale, utilisez la `setMinutes` (méthode).  
  
 Si la valeur d’un argument est supérieure à la plage, ou est un nombre négatif, les autres valeurs stockées sont modifiées en conséquence. Par exemple, si la date stockée est « 5 Jan 1996 00:00:00.00 », et **setUTCMinutes(70)** est appelée, la date est remplacée par « 5 Jan 1996 01:10:00.00. »  
  
 Le **setUTCHours** méthode peut être utilisée pour définir les heures, minutes, secondes et les millisecondes.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `setUTCMinutes` méthode :  
  
```JavaScript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getMinutes, méthode (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes, méthode (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Méthode setMinutes (Date)](../../javascript/reference/setminutes-method-date-javascript.md)