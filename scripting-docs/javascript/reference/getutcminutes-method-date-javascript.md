---
title: "getUTCMinutes, méthode (Date) (JavaScript) | Documents Microsoft"
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
- getUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- UTC times, returning
- getUTCMinutes method
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe691d3b52d18340eeeff81a91c049a262277c54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="getutcminutes-method-date-javascript"></a>getUTCMinutes, méthode (Date) (JavaScript)
Obtient les minutes d’un `Date` à l’aide de temps universel coordonné (UTC) de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un entier compris entre 0 et 59. Retourne que l’heure est inférieure à une minute après l’heure. Si un `Date` objet a été créé sans spécifier l’heure, par défaut, l’heure UTC, valeur de minute est 0. Toutefois, dans les autres fuseaux horaires, il peut être différent.  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir le nombre de minutes exprimé en heure locale, utilisez la `getMinutes` (méthode).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getUTCMinutes`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getMinutes, méthode (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [setMinutes, méthode (Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [Méthode setUTCMinutes (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)