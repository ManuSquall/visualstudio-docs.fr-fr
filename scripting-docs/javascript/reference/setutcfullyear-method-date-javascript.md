---
title: "setUTCFullYear, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCFullYear method
- UTC dates, setting
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dda8b75dd8bc8dac87ea383546f392b064c1d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="setutcfullyear-method-date-javascript"></a>setUTCFullYear, méthode (Date) (JavaScript)
Définit la valeur de l’année dans le `Date` de l’objet à l’aide de temps universel coordonné (UTC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 `numYear`  
 Obligatoire. Valeur numérique égale à l’année.  
  
 `numMonth`  
 Facultatif. Valeur numérique égale au mois. La valeur pour janvier est 0, et valeurs des autres mois suivent consécutifs. Doit être fournie si *argument numDate* est fourni.  
  
 *argument numDate*  
 Facultatif. Une valeur numérique correspondant au jour du mois.  
  
## <a name="remarks"></a>Remarques  
 Tous les **définir** méthodes acceptant des arguments facultatifs utilisent la valeur retournée par correspondant **obtenir** méthodes, si vous ne spécifiez pas un argument facultatif. Par exemple, si le `numMonth` argument n’est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par le `getUTCMonth` (méthode).  
  
 En outre, si la valeur d’un argument est supérieure que sa plage ou est une valeur négative, les autres stockées est modifiées en conséquence.  
  
 Pour définir l’année en heure locale, utilisez la `setFullYear` (méthode).  
  
 La plage d’années pris en charge dans les `Date` objet est d’environ 285 ans à partir de chaque côté de 1970.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setUTCFullYear`.  
  
```JavaScript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getFullYear, méthode (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear, méthode (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Méthode setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)