---
title: Date.Parse, fonction (JavaScript) | Documents Microsoft
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
- parse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parse function [JavaScript]
- Date.parse function [JavaScript]
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a73fda66ef24df17a5213a182c04667fc4dfabf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="dateparse-function-javascript"></a>Date.parse, fonction (JavaScript)
Analyse une chaîne contenant une date et retourne le nombre de millisecondes écoulées entre la date et le 1er janvier 1970 à minuit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Date.parse(dateVal)   
```  
  
## <a name="remarks"></a>Remarques  
 Requis `dateVal` argument est une chaîne contenant une date ou une valeur VT_DATE récupérée à partir d’un objet ActiveX ou autre objet. Pour plus d’informations sur la date des chaînes qui le `Date.parse` fonction peut analyser. consultez [chaînes de Date et heure](../../javascript/date-and-time-strings-javascript.md).  
  
 Le `Date.parse` fonction retourne une valeur entière représentant le nombre de millisecondes écoulées entre le 1er janvier 1970 à minuit et la date fournie dans `dateVal`.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de la fonction `Date.parse`.  
  
```JavaScript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne la différence entre la date indiquée et le 1/1/1970.  
  
```JavaScript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)