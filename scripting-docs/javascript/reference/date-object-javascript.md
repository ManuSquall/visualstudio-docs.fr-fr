---
title: Date, objet (JavaScript) | Documents Microsoft
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
- Date
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, determining
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb5d53f3bddfeb3a3ed1ab36e2b4be822964eba5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641929"
---
# <a name="date-object-javascript"></a>Date, objet (JavaScript)
Permet le stockage de base et la récupération des dates et des heures.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Nom de la variable à laquelle l'objet `Date` est assigné.  
  
 `dateVal`  
 Obligatoire. Si une valeur numérique, `dateVal` représente le nombre de millisecondes en temps universel coordonné entre la date spécifiée et le 1er janvier 1970 à minuit. Si une chaîne, `dateVal` est analysé selon les règles de [chaînes de Date et heure](../../javascript/date-and-time-strings-javascript.md). Le `dateVal` argument peut également être une valeur VT_DATE renvoyé à partir de certains objets ActiveX.  
  
 `year`  
 Obligatoire. L’année complète, par exemple, 1976, (et non 76).  
  
 `month`  
 Obligatoire. Mois sous la forme d’un entier compris entre 0 et 11 (janvier à décembre).  
  
 `date`  
 Obligatoire. La date sous la forme d’un entier compris entre 1 et 31.  
  
 `hours`  
 Facultatif. Doit être fournie si `minutes` est fourni. Un entier compris entre 0 et 23 (minuit à 23 h 00) qui spécifie l’heure.  
  
 minutes  
 Facultatif. Doit être fournie si `seconds` est fourni. Un entier compris entre 0 et 59 qui spécifie les minutes.  
  
 `seconds`  
 Facultatif. Doit être fournie si `milliseconds` est fourni. Un entier compris entre 0 et 59 qui spécifie les secondes.  
  
 `ms`  
 Facultatif. Un entier compris entre 0 et 999 indiquant les millisecondes.  
  
## <a name="remarks"></a>Remarques  
 A `Date` objet contient un nombre représentant un instant particulier dans le temps à une milliseconde. Si la valeur d’un argument est supérieure à sa plage ou est un nombre négatif, les autres valeurs stockées sont modifiées en conséquence. Par exemple, si vous spécifiez 150 secondes, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convertit ce nombre en deux minutes et 30 secondes.  
  
 Si le nombre est `NaN`, l’objet ne représente pas un instant spécifique de temps. Si vous passez sans paramètres pour le `Date` de l’objet, il est initialisé à l’heure actuelle (UTC). Une valeur doit être attribuée à l’objet avant que vous puissiez l’utiliser.  
  
 La plage de dates pouvant être représenté dans un `Date` objet est d’environ 285 années de chaque côté du 1er janvier 1970 à minuit.  
  
 Consultez [du calcul des Dates et heures (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) pour plus d’informations sur l’utilisation de la `Date` objet et les méthodes associées.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de l'objet `Date`.  
  
```JavaScript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## <a name="requirements"></a>Spécifications  
 L'objet `Date object` a été introduit dans [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]. Certains membres des listes suivantes ont été introduits dans les versions ultérieures. Pour plus d’informations, consultez [les informations de Version](../../javascript/reference/javascript-version-information.md) ou consultez la documentation pour les membres individuels.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Date Object`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[constructor, propriété](../../javascript/reference/constructor-property-date.md)|Spécifie la fonction qui crée un objet.|  
|[prototype, propriété](../../javascript/reference/prototype-property-date.md)|Retourne une référence au prototype pour une classe d'objets.|  
  
## <a name="functions"></a>Fonctions  
 Le tableau suivant répertorie les fonctions de l'`Date Object`.  
  
|Fonctions|Description|  
|---------------|-----------------|  
|[Fonction Date.now](../../javascript/reference/date-now-function-javascript.md)|Retourne le nombre de millisecondes écoulées entre le 1er janvier 1970 et la date et heure actuelles.|  
|[Fonction Date.parse](../../javascript/reference/date-parse-function-javascript.md)|Analyse une chaîne contenant une date et retourne le nombre de millisecondes écoulées entre la date et le 1er janvier 1970 à minuit.|  
|[Fonction Date.UTC](../../javascript/reference/date-utc-function-javascript.md)|Retourne le nombre de millisecondes écoulées entre le 1er janvier 1970 à minuit heure universelle coordonnée (UTC) (ou GMT) et la date fournie.|  
  
<a name="js56jsobjdatemeth"></a>   
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'`Date Object`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Méthode getDate](../../javascript/reference/getdate-method-date-javascript.md)|Retourne la valeur de jour du mois en heure locale.|  
|[Méthode getDay](../../javascript/reference/getday-method-date-javascript.md)|Retourne la valeur de jour de semaine en heure locale.|  
|[Méthode getFullYear](../../javascript/reference/getfullyear-method-date-javascript.md)|Retourne la valeur de l’année en heure locale.|  
|[Méthode getHours](../../javascript/reference/gethours-method-date-javascript.md)|Retourne l’heure en heure locale.|  
|[Méthode getMilliseconds](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Retourne la valeur en millisecondes, en heure locale.|  
|[Méthode getMinutes](../../javascript/reference/getminutes-method-date-javascript.md)|Retourne la valeur des minutes en heure locale.|  
|[Méthode getMonth](../../javascript/reference/getmonth-method-date-javascript.md)|Retourne la valeur de mois en heure locale.|  
|[Méthode getSeconds](../../javascript/reference/getseconds-method-date-javascript.md)|Retourne la valeur secondes en heure locale.|  
|[Méthode getTime](../../javascript/reference/gettime-method-date-javascript.md)|Retourne la valeur d’heure dans un `Date` objet en tant que le nombre de millisecondes depuis le 1er janvier 1970 à minuit.|  
|[Méthode getTimezoneOffset](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Retourne la différence en minutes entre l’heure sur l’ordinateur hôte et le temps universel coordonné (UTC).|  
|[Méthode getUTCDate](../../javascript/reference/getutcdate-method-date-javascript.md)|Retourne la valeur de jour du mois à l’aide du format UTC.|  
|[Méthode getUTCDay](../../javascript/reference/getutcday-method-date-javascript.md)|Retourne la valeur de day of week heure UTC.|  
|[Méthode getUTCFullYear](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Retourne la valeur de l’année à l’aide du format UTC.|  
|[Méthode getUTCHours](../../javascript/reference/getutchours-method-date-javascript.md)|Retourne l’heure en UTC.|  
|[Méthode getUTCMilliseconds](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Retourne la valeur de millisecondes à l’aide du format UTC.|  
|[Méthode getUTCMinutes](../../javascript/reference/getutcminutes-method-date-javascript.md)|Retourne la valeur des minutes à l’aide du format UTC.|  
|[Méthode getUTCMonth](../../javascript/reference/getutcmonth-method-date-javascript.md)|Retourne la valeur de mois à l’aide du format UTC.|  
|[Méthode getUTCSeconds](../../javascript/reference/getutcseconds-method-date-javascript.md)|Retourne les secondes en heure UTC.|  
|[Méthode getVarDate](../../javascript/reference/getvardate-method-date-javascript.md)|Retourne la valeur VT_DATE dans un `Date` objet.|  
|[Méthode getYear](../../javascript/reference/getyear-method-date-javascript.md)|Retourne la valeur de l’année.|  
|[Méthode hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet possède une propriété du nom spécifié.|  
|[isPrototypeOf, méthode](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet existe dans la chaîne prototype d'un autre objet.|  
|[Méthode propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retourne une valeur booléenne indiquant si une propriété spécifiée fait partie d'un objet et si elle est énumérable.|  
|[Méthode setDate](../../javascript/reference/setdate-method-date-javascript.md)|Définit le numéro du jour du mois en heure locale.|  
|[Méthode setFullYear](../../javascript/reference/setfullyear-method-date-javascript.md)|Définit la valeur de l’année en heure locale.|  
|[Méthode setHours](../../javascript/reference/sethours-method-date-javascript.md)|Définit la valeur des heures en heure locale.|  
|[Méthode setMilliseconds](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Définit la valeur en millisecondes, en heure locale.|  
|[Méthode setMinutes](../../javascript/reference/setminutes-method-date-javascript.md)|Définit la valeur des minutes en heure locale.|  
|[Méthode setMonth](../../javascript/reference/setmonth-method-date-javascript.md)|Définit la valeur de mois en heure locale.|  
|[Méthode setSeconds](../../javascript/reference/setseconds-method-date-javascript.md)|Définit les secondes en heure locale.|  
|[Méthode setTime](../../javascript/reference/settime-method-date-javascript.md)|Définit la valeur de date et d’heure dans le `Date` objet.|  
|[Méthode setUTCDate](../../javascript/reference/setutcdate-method-date-javascript.md)|Définit le numéro du jour du mois à l’aide du format UTC.|  
|[Méthode setUTCFullYear](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Définit la valeur de l’année à l’aide du format UTC.|  
|[Méthode setUTCHours](../../javascript/reference/setutchours-method-date-javascript.md)|Définit la valeur des heures à l’aide du format UTC.|  
|[Méthode setUTCMilliseconds](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Définit la valeur de millisecondes à l’aide du format UTC.|  
|[Méthode setUTCMinutes](../../javascript/reference/setutcminutes-method-date-javascript.md)|Définit la valeur des minutes à l’aide du format UTC.|  
|[Méthode setUTCMonth](../../javascript/reference/setutcmonth-method-date-javascript.md)|Définit la valeur de mois à l’aide du format UTC.|  
|[Méthode setUTCSeconds](../../javascript/reference/setutcseconds-method-date-javascript.md)|Affecte la valeur secondes à l’aide du format UTC.|  
|[Méthode setYear](../../javascript/reference/setyear-method-date-javascript.md)|Définit la valeur de l’année en heure locale.|  
|[Méthode toDateString](../../javascript/reference/todatestring-method-date-javascript.md)|Retourne une date sous la forme d’une valeur de chaîne.|  
|[Méthode toGMTString](../../javascript/reference/togmtstring-method-date-javascript.md)|Retourne une date convertie en une chaîne à l’aide d’heure de Greenwich (GMT).|  
|[Méthode toISOString](../../javascript/reference/toisostring-method-date-javascript.md)|Retourne une date sous la forme d’une valeur de chaîne au format ISO.|  
|[Méthode toJSON](../../javascript/reference/tojson-method-date-javascript.md)|Utilisé pour transformer les données d’un type d’objet avant la sérialisation JSON.|  
|[Méthode toLocaleDateString](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Retourne une date sous la forme d’une valeur de chaîne appropriée pour les paramètres régionaux de l’environnement hôte.|  
|[toLocaleString, méthode](../../javascript/reference/tolocalestring-date.md)|Retourne un objet converti en une chaîne en utilisant les paramètres régionaux actuels.|  
|[Méthode toLocaleTimeString](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Retourne une heure en tant que valeur de chaîne appropriée pour les paramètres régionaux de l’environnement hôte.|  
|[ToString, méthode](../../javascript/reference/tostring-method-date.md)|Retourne la représentation d'un objet sous forme de chaîne.|  
|[Méthode toTimeString](../../javascript/reference/totimestring-method-date-javascript.md)|Retourne une heure en tant que valeur de chaîne.|  
|[Méthode toUTCString](../../javascript/reference/toutcstring-method-date-javascript.md)|Retourne une date convertie en une chaîne à l’aide du format UTC.|  
|[valueOf, méthode](../../javascript/reference/valueof-method-date.md)|Retourne la valeur primitive de l'objet spécifié.|  
  
## <a name="see-also"></a>Voir aussi  
 [Calcul des Dates et heures (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Chaînes de date et heure](../../javascript/date-and-time-strings-javascript.md)