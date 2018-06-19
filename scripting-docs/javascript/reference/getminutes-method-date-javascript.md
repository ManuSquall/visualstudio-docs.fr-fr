---
title: getMinutes, méthode (Date) (JavaScript) | Documents Microsoft
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
- getMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetMinutes method
- minutes method
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff08fd84345c9ceb816444a1b44643a8353b60b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636769"
---
# <a name="getminutes-method-date-javascript"></a>getMinutes, méthode (Date) (JavaScript)
Obtient les minutes d’un `Date` de l’objet, en heure locale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getMinutes()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un entier compris entre 0 et 59. Retourne que l’heure est inférieure à une minute après l’heure. Si un `Date` objet a été créé sans spécifier l’heure, par défaut, la valeur de minute est 0.  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir la valeur des minutes à l’aide de temps universel coordonné (UTC), utilisez le `getUTCMinutes` (méthode).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment la `getMinutes` (méthode).  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getUTCMinutes, méthode (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes, méthode (Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [Méthode setUTCMinutes (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)