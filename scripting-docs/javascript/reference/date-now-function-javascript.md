---
title: Date.Now, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: now method
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41a098c55b8ced3c630d3724615835301b6f00c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="datenow-function-javascript"></a>Date.now, fonction (JavaScript)
Obtient la date et heure actuelles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Date.now()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Le nombre de millisecondes écoulées entre le 1er janvier 1970 à minuit et la date et heure actuelles.  
  
## <a name="remarks"></a>Remarques  
 Le [méthode getTime](../../javascript/reference/gettime-method-date-javascript.md) retourne le nombre de millisecondes écoulées entre le 1er janvier 1970 et une date spécifiée.  
  
 Pour plus d’informations sur la façon de calculer le temps écoulé et comparer les dates, consultez [du calcul des Dates et heures (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `now`.  
  
```JavaScript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## <a name="requirements"></a>Spécifications  
 Non pris en charge dans les versions installées antérieures à Internet Explorer 9. Toutefois, il est pris en charge dans les modes de document suivants : Quirks, les normes Internet Explorer 6, les normes Internet Explorer 7, les normes Internet Explorer 8, les normes Internet Explorer 9, des normes Internet Explorer 10. Également pris en charge dans [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] applications.  
  
## <a name="see-also"></a>Voir aussi  
 [getTime, méthode (Date)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date (objet)](../../javascript/reference/date-object-javascript.md)   
 [Calcul des Dates et heures (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Méthodes JavaScript](../../javascript/reference/javascript-methods.md)