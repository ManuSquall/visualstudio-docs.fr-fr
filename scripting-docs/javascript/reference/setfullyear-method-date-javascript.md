---
title: setFullYear, méthode (Date) (JavaScript) | Documents Microsoft
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
- setFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setFullYear method
- dates, setting
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5e20a8486d1aefeab9b244c5f1e9d1b1e60c3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640349"
---
# <a name="setfullyear-method-date-javascript"></a>setFullYear, méthode (Date) (JavaScript)
Définit l’année de la `Date` en heure locale de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 `numYear`  
 Obligatoire. Une valeur numérique pour l’année.  
  
 `numMonth`  
 Facultatif. Une valeur numérique base zéro pour le mois (0, 11 janvier décembre). Doit être spécifié si `numDate` est spécifié.  
  
 `numDate`  
 Facultatif. Valeur numérique égale pour le jour du mois.  
  
## <a name="remarks"></a>Remarques  
 Tous les **définir** méthodes acceptant des arguments facultatifs utilisent la valeur retournée par correspondant **obtenir** méthodes, si vous ne spécifiez pas l’argument facultatif. Par exemple, si le `numMonth` argument est facultatif n’est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par la **getMonth** (méthode).  
  
 En outre, si la valeur d’un argument est supérieure à sa plage de calendrier ou est un nombre négative, la date restaure avancer ou reculer comme il convient.  
  
 Pour définir l’année à l’aide de temps universel coordonné (UTC), utilisez le `setUTCFullYear` (méthode).  
  
 La plage d’années pris en charge dans l’objet date est environ 285 années avant et après 1970.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `setFullYear` méthode :  
  
```JavaScript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getFullYear, méthode (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear, méthode (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Méthode setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)