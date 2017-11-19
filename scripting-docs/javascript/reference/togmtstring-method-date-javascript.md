---
title: "toGMTString, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toGMTString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toGMTString method
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cef8a61e04fbb5ada6e03fa946f434327422d9d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="togmtstring-method-date-javascript"></a>toGMTString, méthode (Date) (JavaScript)
Retourne une date convertie en une chaîne à l’aide de Time(GMT) moyenne de Greenwich.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.toGMTString()   
```  
  
## <a name="remarks"></a>Remarques  
 Requis `dateObj` référence est any `Date` objet.  
  
 Le `toGMTString` méthode est obsolète et utilisée uniquement à des fins de compatibilité descendante. Il est recommandé d’utiliser le `toUTCString` méthode à la place.  
  
 Le `toGMTString` méthode retourne un `String` objet qui contient la date de mise en forme selon la convention GMT. Le format de la valeur de retour est le suivant : « 05 Jan 1996 00:00:00 GMT ».  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode toUTCString (Date)](../../javascript/reference/toutcstring-method-date-javascript.md)