---
title: "setTime, méthode (Date) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- SetTime method
- time method
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e66b1fbf5d668330eb727e8bfc50ee9d11a28be3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="settime-method-date-javascript"></a>setTime, méthode (Date) (JavaScript)
Définit la valeur de date et d’heure dans le `Date` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 *millisecondes*  
 Obligatoire. Une valeur numérique représentant le nombre de millisecondes écoulées depuis minuit, le 1er janvier 1970 GMT.  
  
## <a name="remarks"></a>Remarques  
 Si *millisecondes* est négatif, il indique une date antérieure à 1970. La plage de dates disponibles est environ 285 ans à partir de chaque côté de 1970.  
  
 Définition de la date et l’heure avec la `setTime` méthode est indépendante du fuseau horaire.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setTime`.  
  
```JavaScript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getTime (Date)](../../javascript/reference/gettime-method-date-javascript.md)