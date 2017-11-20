---
title: "setMonth, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Month method
- setMonth method
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f2672abebd327af8b0da58d46ebc183b8159711
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="setmonth-method-date-javascript"></a>setMonth, méthode (Date) (JavaScript)
Définit la valeur de mois dans le `Date` en heure locale de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 `numMonth`  
 Obligatoire. Valeur numérique égale au mois. La valeur pour janvier est 0, et valeurs des autres mois suivent consécutifs.  
  
 `dateVal`  
 Facultatif. Une valeur numérique représentant le jour du mois. Si cette valeur n’est pas fournie, la valeur d’un appel à la `getDate` méthode est utilisée.  
  
## <a name="remarks"></a>Remarques  
 Pour définir la valeur de mois à l’aide de temps universel coordonné (UTC), utilisez le `setUTCMonth` (méthode).  
  
 Si la valeur de `numMonth` est supérieure à 11 (janvier correspondant au mois 0) ou est un nombre négatif, l’année stockée est modifiée en conséquence. Par exemple, si la date stockée est « 5 Jan 1996 » et **setMonth(14)** est appelée, la date devient « 5 Mar 1997 ».  
  
 Le **setFullYear** méthode peut être utilisée pour définir l’année, mois et jour du mois.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setMonth`.  
  
```JavaScript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getMonth, méthode (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth, méthode (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Méthode setUTCMonth (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)