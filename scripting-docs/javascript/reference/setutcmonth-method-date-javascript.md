---
title: "setUTCMonth, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCMonth method
- Month method
- UTC dates, setting
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02cb69026b66e3f307a8709ab3f5b23d9518643a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="setutcmonth-method-date-javascript"></a>setUTCMonth, méthode (Date) (JavaScript)
Définit la valeur de mois dans le `Date` de l’objet à l’aide de temps universel coordonné (UTC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 `numMonth`  
 Obligatoire. Valeur numérique égale au mois. La valeur pour janvier est 0, et valeurs des autres mois suivent consécutifs.  
  
 `dateVal`  
 Facultatif. Une valeur numérique représentant le jour du mois. S’il n’est pas fourni, la valeur d’un appel à la `getUTCDate` méthode est utilisée.  
  
## <a name="remarks"></a>Remarques  
 Pour définir la valeur de mois en heure locale, utilisez la `setMonth` (méthode).  
  
 Si la valeur de `numMonth` est supérieure à 11 (janvier correspondant au mois 0), ou est un nombre négatif, l’année stockée est incrémentée ou décrémentée en conséquence. Par exemple, si la date stockée est « 5 Jan 1996 00:00:00.00 », et **setUTCMonth(14)** est appelée, la date est modifiée en « Mar 5, 1997 00:00:00.00. »  
  
 Le **setUTCFullYear** méthode peut être utilisée pour définir l’année, mois et jour du mois.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setUTCMonth`.  
  
```JavaScript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getMonth, méthode (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth, méthode (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Méthode setMonth (Date)](../../javascript/reference/setmonth-method-date-javascript.md)