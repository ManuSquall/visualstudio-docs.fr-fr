---
title: "getMonth, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, month value
- Month method
- GetMonth method
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeffd7ffc7bee5fa63607e342a9a9dced7088d35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="getmonth-method-date-javascript"></a>getMonth, méthode (Date) (JavaScript)
Obtient le mois, en heure locale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getMonth()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Le `getMonth` méthode retourne un entier compris entre 0 (janvier) et 11 (décembre). Pour un `Date` construit avec « 5 Jan 1996 », `getMonth` retourne 0.  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir la valeur de mois à l’aide de temps universel coordonné (UTC), utilisez le `getUTCMonth` (méthode).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getMonth`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getUTCMonth, méthode (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth, méthode (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Méthode setUTCMonth (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)