---
title: "toTimeString, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toTimeString method
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d9af1f688fee0c066158d8504e00f22af9b3a21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="totimestring-method-date-javascript"></a>toTimeString, méthode (Date) (JavaScript)
Retourne une heure en tant que valeur de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
objDate. toTimeString( )  
```  
  
## <a name="remarks"></a>Remarques  
 La référence `objDate` nécessaire est un objet `Date`.  
  
 Le `toTimeString` méthode retourne une valeur de chaîne contenant l’heure dans le fuseau horaire actuel.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, l’heure est définie à 2 000 millisecondes après minuit le 1er janvier 1970 UTC, puis il est écrit.  
  
```JavaScript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [toDateString, méthode (Date)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [Méthode toLocaleTimeString (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)