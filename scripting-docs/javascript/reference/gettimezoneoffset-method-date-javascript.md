---
title: "getTimezoneOffset, méthode (Date) (JavaScript) | Documents Microsoft"
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
- getTimeZoneOffset
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getTimezoneOffset method
- time zones [Visual Studio]
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e49a3c8b7060e6097300f8aaf99b2ef869833018
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="gettimezoneoffset-method-date-javascript"></a>getTimezoneOffset, méthode (Date) (JavaScript)
Obtient la différence en minutes entre l’heure sur l’ordinateur local et le temps universel coordonné (UTC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### <a name="parameters"></a>Paramètres  
 La référence `dateObj` nécessaire est un objet `Date` .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne le nombre de minutes entre l’heure sur l’ordinateur actuel (l’ordinateur client ou, si cette méthode est appelée à partir d’un serveur, l’ordinateur du serveur) et l’heure UTC. Il est positive si l’heure locale de l’ordinateur actuel se trouve derrière UTC (par exemple, heure du Pacifique) et négative si l’heure locale de l’ordinateur actuel est avant l’heure UTC (par exemple, le Japon). Si un serveur à New York City est contacté par un client à Los Angeles le 1er décembre `getTimezoneOffset` retourne 480 si exécutée sur le client ou 300 si exécutée sur le serveur.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getTimezoneOffset`.  
  
```JavaScript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getTime (Date)](../../javascript/reference/gettime-method-date-javascript.md)