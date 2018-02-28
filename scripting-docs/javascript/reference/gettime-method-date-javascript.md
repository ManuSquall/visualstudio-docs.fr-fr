---
title: "getTime, méthode (Date) (JavaScript) | Documents Microsoft"
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
- getTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetTime method
- time method
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a31e542445e89a0e2f3364d36ae44f8d2d4cf9bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="gettime-method-date-javascript"></a>getTime, méthode (Date) (JavaScript)
Obtient la valeur de temps en millisecondes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getTime()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne le nombre de millisecondes écoulées entre le 1er janvier 1970 à minuit et la valeur d’heure dans le `Date` objet. La plage de dates est approximativement de 285 ans à partir de chaque côté du 1er janvier 1970 à minuit. Les nombres négatifs indiquent des dates antérieures à 1970.  
  
## <a name="remarks"></a>Remarques  
 Lorsque vous effectuez plusieurs calculs de date et d’heure, vous voudrez probablement définir des variables égales au nombre de millisecondes dans un jour, heure ou minute. Exemple :  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 Consultez [du calcul des Dates et heures (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) pour plus d’informations sur l’utilisation de la `getTime` (méthode).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getTime`.  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setTime (Date)](../../javascript/reference/settime-method-date-javascript.md)