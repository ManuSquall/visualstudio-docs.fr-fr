---
title: "Date, objet (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Date"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objet)"
  - "dates, déterminer"
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# Date, objet (JavaScript)
Permet le stockage et la récupération de base de dates et d'heures.  
  
## Syntaxe  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## Paramètres  
 `dateObj`  
 Requis.  Nom de la variable à laquelle l'objet `Date` est assigné.  
  
 `dateVal`  
 Requis.  S'il s'agit d'une valeur numérique, `dateVal` représente le nombre de millisecondes en temps universel coordonné entre la date spécifiée et le 1er janvier 1970 à minuit.  S'il s'agit d'une chaîne, l'analyse de `dateVal` est effectuée en respectant les règles de [Chaînes de date et heure](../../javascript/date-and-time-strings-javascript.md).  L'argument `dateVal` peut également être une valeur VT\_DATE telle que celle retournée par des objets ActiveX.  
  
 `year`  
 Requis.  L'année complète, par exemple 1976 \(et non 76\).  
  
 `month`  
 Requis.  Mois, représenté par un entier compris entre 0 et 11 \(janvier à décembre\).  
  
 `date`  
 Requis.  Date, représentée par un entier compris entre 1 et 31.  
  
 `hours`  
 Optionnel.  Doit être fournie si l'argument `minutes` est spécifié.  Entier compris entre 0 et 23 \(minuit à 23 heures\) indiquant l'heure.  
  
 minutes  
 Optionnel.  Doit être fournie si l'argument `seconds` est spécifié.  Entier compris entre 0 et 59 indiquant les minutes.  
  
 `seconds`  
 Optionnel.  Doit être fournie si l'argument `milliseconds` est spécifié.  Entier compris entre 0 et 59 indiquant les secondes.  
  
 `ms`  
 Optionnel.  Entier compris entre 0 et 999 indiquant les millisecondes.  
  
## Notes  
 Un objet `Date` contient un nombre indiquant un instant déterminé avec une précision de l'ordre de la milliseconde.  Si la valeur d'un argument est en dehors de la plage de sélection ou si elle est négative, les autres valeurs stockées sont modifiées en conséquence.  Par exemple, si vous spécifiez 150 secondes, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convertit ce nombre en deux minutes et trente secondes.  
  
 Si le nombre est `NaN`, l'objet ne représente pas un instant précis.  Si aucun paramètre n'est passé à l'objet `Date`, celui\-ci est initialisé conformément à l'heure actuelle \(temps universel, UTC\).  L'objet doit avoir une valeur avant de pouvoir l'utiliser.  
  
 La plage de dates pouvant être représentée dans un objet `Date` couvre environ 285 616 années, avant et après le 1er janvier 1970.  
  
 Consultez [Calcul des dates et des heures \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md) pour plus d'informations sur l'utilisation de l'objet `Date` et méthodes connexes.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de l'objet `Date`.  
  
```javascript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## Configuration requise  
 L'objet `Date object` a été introduit dans [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  Certains membres des listes suivantes ont été introduits dans les versions ultérieures.  Pour plus d'informations, consultez [Informations sur la version](../../javascript/reference/javascript-version-information.md) ou la documentation relative aux différents membres.  
  
## Propriétés  
 Le tableau suivant répertorie les propriétés de l'`Date Object`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[constructor, propriété](../../javascript/reference/constructor-property-date.md)|Spécifie la fonction qui crée un objet.|  
|[prototype, propriété](../../javascript/reference/prototype-property-date.md)|Retourne une référence au prototype pour une classe d'objets.|  
  
## Fonctions  
 Le tableau suivant répertorie les fonctions de l'`Date Object`.  
  
|Fonctions|Description|  
|---------------|-----------------|  
|[Fonction Date.now](../../javascript/reference/date-now-function-javascript.md)|Retourne le nombre de millisecondes écoulées entre le 1er janvier 1970 et la date et l'heure actuelles.|  
|[Fonction Date.parse](../../javascript/reference/date-parse-function-javascript.md)|Analyse une chaîne contenant une date et retourne le nombre de millisecondes entre cette date et le 1er janvier 1970 à minuit.|  
|[Date.UTC, fonction](../../javascript/reference/date-utc-function-javascript.md)|Retourne le nombre de millisecondes entre le 1er janvier 1970 à minuit, selon le temps universel \(ou selon l'heure GMT\) et la date fournie.|  
  
<a name="js56jsobjdatemeth"></a>   
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'`Date Object`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[getDate, méthode](../../javascript/reference/getdate-method-date-javascript.md)|Retourne la valeur jour du mois à l'aide de l'heure locale.|  
|[getDay, méthode](../../javascript/reference/getday-method-date-javascript.md)|Retourne le jour de la semaine en heure locale.|  
|[getFullYear, méthode](../../javascript/reference/getfullyear-method-date-javascript.md)|Retourne l'année en heure locale.|  
|[getHours, méthode](../../javascript/reference/gethours-method-date-javascript.md)|Retourne les heures en heure locale.|  
|[getMilliseconds, méthode](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Retourne les millisecondes en heure locale.|  
|[getMinutes, méthode](../../javascript/reference/getminutes-method-date-javascript.md)|Retourne les minutes en heure locale.|  
|[getMonth, méthode](../../javascript/reference/getmonth-method-date-javascript.md)|Retourne le mois en heure locale.|  
|[getSeconds, méthode](../../javascript/reference/getseconds-method-date-javascript.md)|Retourne les secondes en heure locale.|  
|[getTime, méthode](../../javascript/reference/gettime-method-date-javascript.md)|Retourne l'heure d'un objet `Date`, en tant que nombre de millisecondes écoulées depuis le 1er janvier 1970 à minuit.|  
|[getTimezoneOffset, méthode](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Retourne la différence en minutes entre l'heure de l'ordinateur hôte et l'heure UTC.|  
|[getUTCDate, méthode](../../javascript/reference/getutcdate-method-date-javascript.md)|Retourne le jour du mois au format UTC.|  
|[getUTCDay, méthode](../../javascript/reference/getutcday-method-date-javascript.md)|Retourne le jour de la semaine au format UTC.|  
|[getUTCFullYear, méthode](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Retourne l'année au format UTC.|  
|[getUTCHours, méthode](../../javascript/reference/getutchours-method-date-javascript.md)|Retourne les heures au format UTC.|  
|[getUTCMilliseconds, méthode](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Retourne les millisecondes au format UTC.|  
|[getUTCMinutes, méthode](../../javascript/reference/getutcminutes-method-date-javascript.md)|Retourne les minutes au format UTC.|  
|[getUTCMonth, méthode](../../javascript/reference/getutcmonth-method-date-javascript.md)|Retourne le mois au format UTC.|  
|[getUTCSeconds, méthode](../../javascript/reference/getutcseconds-method-date-javascript.md)|Retourne les secondes au format UTC.|  
|[getVarDate, méthode](../../javascript/reference/getvardate-method-date-javascript.md)|Retourne la valeur VT\_DATE d'un objet `Date`.|  
|[getYear, méthode](../../javascript/reference/getyear-method-date-javascript.md)|Retourne l'année.|  
|[hasOwnProperty, méthode](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet possède une propriété du nom spécifié.|  
|[isPrototypeOf, méthode](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet existe dans la chaîne prototype d'un autre objet.|  
|[Méthode propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retourne une valeur booléenne indiquant si une propriété spécifiée fait partie d'un objet et si elle est énumérable.|  
|[setDate, méthode](../../javascript/reference/setdate-method-date-javascript.md)|Définit le numéro du jour du mois en heure locale.|  
|[setFullYear, méthode](../../javascript/reference/setfullyear-method-date-javascript.md)|Définit l'année en heure locale.|  
|[setHours, méthode](../../javascript/reference/sethours-method-date-javascript.md)|Définit les heures en heure locale.|  
|[setMilliseconds, méthode](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Définit les millisecondes en heure locale.|  
|[setMinutes, méthode](../../javascript/reference/setminutes-method-date-javascript.md)|Définit les minutes en heure locale.|  
|[setMonth, méthode](../../javascript/reference/setmonth-method-date-javascript.md)|Définit le mois en heure locale.|  
|[setSeconds, méthode](../../javascript/reference/setseconds-method-date-javascript.md)|Définit les secondes en heure locale.|  
|[setTime, méthode](../../javascript/reference/settime-method-date-javascript.md)|Définit la date et l'heure dans l'objet `Date`.|  
|[setUTCDate, méthode](../../javascript/reference/setutcdate-method-date-javascript.md)|Définit le numéro du jour du mois au format UTC.|  
|[setUTCFullYear, méthode](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Définit l'année au format UTC.|  
|[setUTCHours, méthode](../../javascript/reference/setutchours-method-date-javascript.md)|Définit les heures au format UTC.|  
|[setUTCMilliseconds, méthode](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Définit les millisecondes au format UTC.|  
|[setUTCMinutes, méthode](../../javascript/reference/setutcminutes-method-date-javascript.md)|Définit les minutes au format UTC.|  
|[setUTCMonth, méthode](../../javascript/reference/setutcmonth-method-date-javascript.md)|Définit le mois au format UTC.|  
|[setUTCSeconds, méthode](../../javascript/reference/setutcseconds-method-date-javascript.md)|Définit les secondes au format UTC.|  
|[setYear, méthode](../../javascript/reference/setyear-method-date-javascript.md)|Définit l'année en heure locale.|  
|[toDateString, méthode](../../javascript/reference/todatestring-method-date-javascript.md)|Retourne une date en tant que valeur de chaîne.|  
|[toGMTString, méthode](../../javascript/reference/togmtstring-method-date-javascript.md)|Retourne une date convertie en chaîne en utilisant la convention GMT.|  
|[toISOString, méthode](../../javascript/reference/toisostring-method-date-javascript.md)|Retourne une date sous forme de valeur de chaîne au format ISO.|  
|[toJSON, méthode](../../javascript/reference/tojson-method-date-javascript.md)|Utilisée pour transformer les données d'un type d'objet avant la sérialisation JSON.|  
|[toLocaleDateString, méthode](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Retourne une date convertie en valeur de chaîne en fonction des paramètres régionaux définis pour l'environnement hôte.|  
|[toLocaleString, méthode](../../javascript/reference/tolocalestring-date.md)|Retourne un objet converti en chaîne, à l'aide des paramètres régionaux actuels.|  
|[toLocaleTimeString, méthode](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Retourne une valeur horaire convertie en valeur de chaîne en fonction des paramètres régionaux définis pour l'environnement hôte.|  
|[toString, méthode](../../javascript/reference/tostring-method-date.md)|Retourne la représentation d'un objet sous forme de chaîne.|  
|[toTimeString, méthode](../../javascript/reference/totimestring-method-date-javascript.md)|Retourne une valeur horaire sous forme de valeur de chaîne.|  
|[toUTCString, méthode](../../javascript/reference/toutcstring-method-date-javascript.md)|Retourne une date convertie en chaîne selon le format UTC.|  
|[valueOf, méthode](../../javascript/reference/valueof-method-date.md)|Retourne la valeur primitive de l'objet spécifié.|  
  
## Voir aussi  
 [Calcul des dates et des heures \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Chaînes de date et heure](../../javascript/date-and-time-strings-javascript.md)