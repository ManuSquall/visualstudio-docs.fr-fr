---
title: getUTCFullYear, méthode (Date) (JavaScript) | Documents Microsoft
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
- getUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getUTCFullYear method
- Date object
- UTCFullYear method
- dates, UTC
- UTC dates, returning
- Full Year method
- UTC dates, getting
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8268631a96eed1f61ef4ba908b78680c8522096
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636849"
---
# <a name="getutcfullyear-method-date-javascript"></a>getUTCFullYear, méthode (Date) (JavaScript)
Obtient l’année à l’aide de temps universel coordonné (UTC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’année sous la forme d’un nombre à quatre chiffres. Années spécifié à deux chiffres dans le `Date` constructeur ou en `setFullYear` sont censées pour être au vingtième siècle, étant donné la « 5/14/12 », `getUTCFullYear` retourne « 1912 ».  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir l’année en heure locale, utilisez la `getFullYear` (méthode).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getUTCFullYear`.  
  
```JavaScript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getFullYear, méthode (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [setFullYear, méthode (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Méthode setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)