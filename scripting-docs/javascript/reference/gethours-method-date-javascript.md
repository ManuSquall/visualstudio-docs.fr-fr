---
title: getHours, méthode (Date) (JavaScript) | Documents Microsoft
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
- getHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- GetHours method
- Hours method
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87170f96ee6ae6b4a825436717a94749cc336ee0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636619"
---
# <a name="gethours-method-date-javascript"></a>getHours, méthode (Date) (JavaScript)
Obtient les heures dans une date, heure locale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getHours()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Un entier compris entre 0 et 23, qui indique le nombre d’heures depuis minuit. Valeur zéro est renvoyée si l’heure est antérieure à 1:00:00. Si un `Date` objet a été créé sans spécifier l’heure, par défaut, l’heure est 0.  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir la valeur des heures à l’aide de temps universel coordonné (UTC), utilisez le `getUTCHours` (méthode).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getHours`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getUTCHours, méthode (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours, méthode (Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [Méthode setUTCHours (Date)](../../javascript/reference/setutchours-method-date-javascript.md)