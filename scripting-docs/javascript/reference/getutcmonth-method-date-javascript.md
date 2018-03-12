---
title: "getUTCMonth, méthode (Date) (JavaScript) | Documents Microsoft"
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
- getUTCMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- UTC dates, returning
- Month method
- getUTCMonth method
ms.assetid: eabae139-4da0-4e4a-a4cb-608e6375fc9e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07e7ecdc9a9ee8a49c12fc65e4b2ba1056bd377c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="getutcmonth-method-date-javascript"></a>getUTCMonth, méthode (Date) (JavaScript)
Obtient le mois d’un `Date` à l’aide de temps universel coordonné (UTC) de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getUTCMonth()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un entier compris entre 0 (janvier) et 11 (décembre).  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir le mois en heure locale, utilisez la **getMonth** (méthode).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getUTCMonth`.  
  
```JavaScript  
var date = new Date("2/2/2002");  
document.write(date.getUTCMonth());  
  
// Output: 1  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getMonth, méthode (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [setMonth, méthode (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Méthode setUTCMonth (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)