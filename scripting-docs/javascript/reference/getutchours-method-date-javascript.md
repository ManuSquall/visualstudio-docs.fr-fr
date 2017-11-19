---
title: "getUTCHours, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- UTC times, returning
- getUTCHours method
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34a07f9f63fe22d3101cc748e9dde978385a71ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="getutchours-method-date-javascript"></a>getUTCHours, méthode (Date) (JavaScript)
Obtient la valeur des heures dans un `Date` de l’objet à l’aide de temps universel coordonné (UTC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un entier compris entre 0 et 23 indiquant le nombre d’heures écoulées depuis minuit. Valeur zéro est renvoyée si l’heure est antérieure à 1:00:00. Si un `Date` objet a été créé sans spécifier l’heure, par défaut l’heure est 0 en temps UTC. Cette durée peut être différente de zéro dans les autres fuseaux horaires.  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir le nombre d’heures écoulées depuis minuit en heure locale, utilisez la `getHours` (méthode).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getUTCHours`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(datee.getUTCHours());  
  
// Output (in the PST time zone):  
// 8  
// 19  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getHours, méthode (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [setHours, méthode (Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [Méthode setUTCHours (Date)](../../javascript/reference/setutchours-method-date-javascript.md)