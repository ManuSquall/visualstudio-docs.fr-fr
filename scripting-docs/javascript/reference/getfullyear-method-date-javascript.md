---
title: getFullYear, méthode (Date) (JavaScript) | Documents Microsoft
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
- getFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- Date object
- getFullYear method
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 211d6c86435e39eb75b9b1ce3415738541ca07db
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636749"
---
# <a name="getfullyear-method-date-javascript"></a>getFullYear, méthode (Date) (JavaScript)
Obtient l’année, en heure locale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getFullYear()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Année, en tant que nombre à quatre chiffres. Par exemple, l’année 1976 est retournée sous la forme 1976. Années spécifié à deux chiffres dans le `Date` constructeur ou en `setFullYear` sont censées pour être au vingtième siècle, étant donné la « 5/14/12 », `getFullYear` retourne « 1912 ».  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir l’année à l’aide de temps universel coordonné (UTC), utilisez le `getUTCFullYear` (méthode).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **getFullYear** (méthode).  
  
```JavaScript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getUTCFullYear, méthode (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear, méthode (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Méthode setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)