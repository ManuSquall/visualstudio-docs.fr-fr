---
title: "getMilliseconds, méthode (Date) (JavaScript) | Documents Microsoft"
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
- getMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- getMilliseconds method
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33e5fc54dffbe06e47f0978e6cef94b1f650c90f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="getmilliseconds-method-date-javascript"></a>getMilliseconds, méthode (Date) (JavaScript)
Obtient les millisecondes d’une Date, heure locale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne les millisecondes, d’une date. La valeur peut être comprise entre 0 et 999. Si une date a été construite sans spécifier les temps en millisecondes, la valeur retournée est 0.  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir le nombre de millisecondes en temps universel coordonné (UTC), utilisez le `getUTCMilliseconds` (méthode).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le **getMilliseconds** (méthode).  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getUTCMilliseconds, méthode (Date)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds, méthode (Date)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [Méthode setUTCMilliseconds (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)