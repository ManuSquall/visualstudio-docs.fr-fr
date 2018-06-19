---
title: setMinutes, méthode (Date) (JavaScript) | Documents Microsoft
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
- setMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- setMinutes method
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce40cb3ebf769cdd8f668e246e272833780434d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641189"
---
# <a name="setminutes-method-date-javascript"></a>setMinutes, méthode (Date) (JavaScript)
Définit la valeur des minutes le **Date** en heure locale de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Tout objet `Date`.  
  
 `numMinutes`  
 Obligatoire. Valeur numérique égale à la valeur des minutes. Doit être fourni si un des arguments suivants est utilisé.  
  
 *numSeconds n'*  
 Facultatif. Valeur numérique égale à la valeur des secondes. Doit être fournie si le `numMilli` argument est utilisé.  
  
 `numMilli`  
 Facultatif. Valeur numérique égale à la valeur en millisecondes.  
  
## <a name="remarks"></a>Remarques  
 Tous les **définir** méthodes acceptant des arguments facultatifs utilisent la valeur retournée par correspondant **obtenir** méthodes, si vous ne spécifiez pas un argument facultatif. Par exemple, si le *numSeconds ne* argument non spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par le `getSeconds` (méthode).  
  
 Pour définir la valeur des minutes à l’aide de temps universel coordonné (UTC), utilisez le `setUTCMinutes` (méthode).  
  
 Si la valeur d’un argument est supérieure à sa plage ou est un nombre négatif, les autres valeurs stockées sont modifiées en conséquence. Par exemple, si la date stockée est « Jan 5, 1996 00:00:00 » et **setMinutes(90)** est appelée, la date est modifiée en « le 5 janvier 1996 01:30:00. » Les nombres négatifs ont un comportement similaire.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setMinutes`.  
  
```JavaScript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getMinutes, méthode (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes, méthode (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Méthode setUTCMinutes (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)