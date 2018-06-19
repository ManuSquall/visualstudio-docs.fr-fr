---
title: getSeconds, méthode (Date) (JavaScript) | Documents Microsoft
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
- getSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- seconds method
- GetSeconds method
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 151d720b92fb9d7068c320983a25b965078f1b2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636779"
---
# <a name="getseconds-method-date-javascript"></a>getSeconds, méthode (Date) (JavaScript)
Obtient les secondes d’une `Date` de l’objet, en heure locale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getSeconds()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un entier compris entre 0 et 59. Zéro est retourné lorsque l’heure est inférieure à une seconde dans la minute en cours. Si un `Date` objet a été créé sans spécifier l’heure, par défaut, la valeur des secondes est 0.  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir les secondes en temps universel coordonné (UTC), utilisez le `getUTCSeconds` (méthode).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getSeconds`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getUTCSeconds, méthode (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds, méthode (Date)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [Méthode setUTCSeconds (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)