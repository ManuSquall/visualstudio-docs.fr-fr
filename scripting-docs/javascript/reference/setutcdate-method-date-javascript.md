---
title: "setUTCDate, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- dates, setting
- UTC dates, setting
- setUTCDate method
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5631a36c8b1c4f1ee50dcadb39f0f21ae5aa28e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="setutcdate-method-date-javascript"></a>setUTCDate, méthode (Date) (JavaScript)
Définit le numéro du jour du mois dans le `Date` de l’objet à l’aide de temps universel coordonné (UTC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 *argument numDate*  
 Obligatoire. Une valeur numérique correspondant au jour du mois.  
  
## <a name="remarks"></a>Remarques  
 Pour définir le jour du mois en heure locale, utilisez la `setDate` (méthode).  
  
 Si la valeur de *argument numDate* est supérieur au nombre de jours du mois stocké dans le **Date** de l’objet ou est un nombre négatif, la date est définie à une date égale à *argument numDate* moins le nombre de jours dans le mois stocké. Par exemple, si la date stockée est le 5 janvier 1996, et **setUTCDate(32)** est appelée, la date change au 1er février 1996. Les nombres négatifs ont un comportement similaire.  
  
 Le **setUTCFullYear** méthode peut être utilisée pour définir l’année, mois et jour du mois.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setUTCDate`.  
  
```JavaScript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getDate, méthode (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [GETUTCDATE, méthode (Date)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [Méthode setDate (Date)](../../javascript/reference/setdate-method-date-javascript.md)