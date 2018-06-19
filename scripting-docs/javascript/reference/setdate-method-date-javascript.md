---
title: setDate, méthode (Date) (JavaScript) | Documents Microsoft
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
- setDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setDate method
- dates, setting
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d74340287b3a7348419d302f79775eb610c6983
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640309"
---
# <a name="setdate-method-date-javascript"></a>setDate, méthode (Date) (JavaScript)
Définit la valeur numérique de jour du mois de la `Date` en heure locale de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 `numDate`  
 Obligatoire. Une valeur numérique correspondant au jour du mois.  
  
## <a name="remarks"></a>Remarques  
 Pour définir la valeur de jour du mois à l’aide de temps universel coordonné (UTC), utilisez le `setUTCDate` (méthode).  
  
 Si la valeur de `numDate` est supérieur au nombre de jours du mois, la date restaure sur un mois et/ou l’année ultérieure. Par exemple, si la date stockée est le 5 janvier 1996 et `setDate(32)` est appelée, la date change au 1er février 1996. Si `numDate` est un nombre négatif, la date restaure un mois et/ou une année antérieure. Par exemple, si la date stockée est le 5 janvier 1996 et `setDate(-32)` est appelée, la date change pour le 29 novembre 1995.  
  
 Le [setFullYear, méthode (Date)](../../javascript/reference/setfullyear-method-date-javascript.md) peut être utilisé pour définir l’année, mois et jour du mois.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setDate`.  
  
```JavaScript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getDate, méthode (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setFullYear, méthode (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setMonth, méthode (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Méthode setUTCDate (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)