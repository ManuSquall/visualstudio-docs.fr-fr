---
title: Date.UTC, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: UTC
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC function [JavaScript]
- UTC dates, returning
- Date.UTC function [JavaScript]
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6a7c5622b74699e3d718ceb65e96638bdb6c3c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="dateutc-function-javascript"></a>Date.UTC, fonction (JavaScript)
Retourne le nombre de millisecondes écoulées entre le 1er janvier 1970 à minuit heure universelle coordonnée (UTC) (ou GMT) et la date spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Paramètres  
 `year`  
 Obligatoire. La désignation de l’année complète est requise pour les dates entre siècle. Si `year` est comprise entre 0 et 99 est utilisé, `year` est censé pour être 1900 + `year`.  
  
 `month`  
 Obligatoire. Mois sous la forme d’un entier compris entre 0 et 11 (janvier à décembre).  
  
 `day`  
 Obligatoire. La date sous la forme d’un entier compris entre 1 et 31.  
  
 `hours`  
 Facultatif. Doit être fournie si `minutes` est fourni. Un entier compris entre 0 et 23 (minuit à 23 h 00) qui spécifie l’heure.  
  
 `minutes`  
 Facultatif. Doit être fournie si `seconds` est fourni. Un entier compris entre 0 et 59 qui spécifie les minutes.  
  
 `seconds`  
 Facultatif. Doit être fournie si `milliseconds` est fourni. Un entier compris entre 0 et 59 qui spécifie les secondes.  
  
 `ms`  
 Facultatif. Un entier compris entre 0 et 999 indiquant les millisecondes.  
  
## <a name="remarks"></a>Remarques  
 Le `Date.UTC` fonction retourne le nombre de millisecondes écoulées entre l’heure UTC du 1er janvier 1970 à minuit et la date fournie. Cette valeur de retour peut être utilisée dans le `setTime` (méthode) et dans le `Date` constructeur d’objet. Si la valeur d’un argument est supérieure à la plage, ou est un nombre négatif, les autres valeurs stockées sont modifiées en conséquence. Par exemple, si vous spécifiez 150 secondes, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convertit ce nombre en deux minutes et 30 secondes.  
  
 La différence entre la `Date.UTC` (fonction) et le `Date` constructeur d’objet qui accepte une date est que la `Date.UTC` fonction suppose que l’heure UTC et le `Date` constructeur d’objet suppose que l’heure locale.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de la fonction `Date.UTC`.  
  
```JavaScript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setTime (Date)](../../javascript/reference/settime-method-date-javascript.md)