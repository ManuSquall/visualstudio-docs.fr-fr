---
title: "Chaînes de date/heure (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba0798c5-3574-4434-89f4-3d90be276001
caps.latest.revision: "47"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6218ba273b26243382d1e825b6da961d604917ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="date-and-time-strings-javascript"></a>Chaînes de date/heure (JavaScript)
Vous pouvez utiliser un certain nombre de techniques pour spécifier et mettre en forme les chaînes de date et d'heure JavaScript.  
  
## <a name="formatting-dates-using-intldatetimeformat"></a>Mise en forme des dates avec Intl.DateTimeFormat  
 Internet Explorer 11 propose la prise en charge de l’objet [Intl.DateTimeFormat](../javascript/reference/intl-datetimeformat-object-javascript.md), qui fait partie de la [spécification de l’API ECMAScript Internationalization](http://www.ecma-international.org/ecma-402/1.0/). Pour mettre en forme des dates, vous pouvez utiliser cet objet directement, ou vous pouvez utiliser l’implémentation mise à jour de [toLocaleDateString, méthode (Date)](../javascript/reference/tolocaledatestring-method-date-javascript.md) et [toLocaleTimeString, méthode (Date)](../javascript/reference/tolocaletimestring-method-date-javascript.md). Ces méthodes [d’objet de date](../javascript/reference/date-object-javascript.md) utilisent `Intl.DateTimeFormat` en interne pour prendre en charge les nouveaux paramètres optionnels pour les paramètres régionaux et autres options de mise en forme.  
  
 L'exemple suivant montre comment utiliser `toLocaleDateString` et `toLocaleTimeString` pour mettre en forme les dates et heures. Le premier paramètre passé à ces méthodes est une valeur de paramètre régional, par exemple « en-us ». Le deuxième paramètre, s'il est présent, spécifie les options de mise en forme, telles que la forme longue du jour de la semaine.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = {  
    weekday: "long", year: "numeric", month: "short",  
    day: "numeric", hour: "2-digit", minute: "2-digit"  
};  
  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleTimeString("en-us", options));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleTimeString("ja-JP", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013  
// ‎Friday‎, ‎Feb‎ ‎1‎, ‎2013‎ ‎06‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎  
// ‎2013‎年‎2‎月‎1‎日 ‎金曜日‎ ‎06‎:‎00  
```  
  
 Pour obtenir la liste complète des options de mise en forme, consultez [Intl.DateTimeFormat Object](../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
## <a name="formatting-dates"></a>Mise en forme des dates  
 Avant Internet Explorer 11, JavaScript ne disposait pas de méthodes spécifiques pour mettre en forme les dates et heures. Pour fournir votre propre mise en forme des dates pour les versions antérieures du navigateur, utilisez les méthodes [getDay (Date)](../javascript/reference/getday-method-date-javascript.md), [getDate (Date)](../javascript/reference/getdate-method-date-javascript.md), [getMonth (Date)](../javascript/reference/getmonth-method-date-javascript.md) et [getFullYear (Date)](../javascript/reference/getfullyear-method-date-javascript.md). (La méthode [getYear (Date)](../javascript/reference/getyear-method-date-javascript.md) est obsolète et ne doit pas être utilisée.)  
  
```JavaScript  
var myDate = new Date("February 3, 2001");  
var myDate = new Date("February 3 2001");  
document.write((myDate.getMonth() + 1) + "-" + myDate.getDate() + "-" + myDate.getFullYear());  
document.write("<br/>");  
document.write((myDate.getMonth() + 1) + "/" + myDate.getDate() + "/" + myDate.getFullYear());  
  
//Output:  
// 2-3-2001  
// 2/3/2001  
```  
  
 Vous pouvez fournir votre propre mise en forme de l’heure à l’aide des méthodes [getHours (Date)](../javascript/reference/gethours-method-date-javascript.md), [getMinutes (Date)](../javascript/reference/getminutes-method-date-javascript.md), [getSeconds (Date)](../javascript/reference/getseconds-method-date-javascript.md) et [ getMilliseconds (Date)](../javascript/reference/getmilliseconds-method-date-javascript.md).  
  
```JavaScript  
myDate = new Date();  
myDate.setHours(10, 30, 53, 400);  
  
document.write(myDate.getHours() + ":" + myDate.getMinutes() + ":" + myDate.getSeconds() +   
":" + myDate.getMilliseconds());  
  
// Output:   
// 10:30:53:400  
```  
  
## <a name="converting-strings-to-dates"></a>Conversion de chaînes en dates  
 Vous pouvez indiquer des chaînes pour construire les objets `Date` avec `Date(dateStr)` ou avec  `Date.parse(dateStr)`. JavaScript utilise les règles suivantes pour analyser les chaînes de date :  
  
-   Tout d’abord, il essaie d’analyser une chaîne de date en utilisant le [format de date ISO](#ISO).  
  
    > [!NOTE]
    >  JavaScript utilise une version simplifiée du format étendu ISO 8601.  
  
-   Si la chaîne de date n’est pas au format ISO, JavaScript essaie d’analyser la date en utilisant [d’autres formats de date](#OtherDateFormats).  
  
<a name="ISO"></a>   
## <a name="iso-date-format"></a>Format de date ISO  
 Le format ISO est une version simplifiée du format ISO 8601 étendu. Le format est le suivant :  
  
 `YYYY-MM-DDTHH:mm:ss.sssZ`  
  
> [!IMPORTANT]
>  Le format de date ISO n'est pris en charge ni par Internet Explorer 8 (mode normes) ni par le mode Quirks.  
  
 Le tableau suivant décrit la façon dont se compose ce format.  
  
|Symbole|Description|Valeurs|  
|------------|-----------------|------------|  
|`-`, `:`, `.`, `T`|Caractères réellement dans la chaîne. `T` spécifie le début d'une heure.||  
|`YYYY`|Année. L'année peut être exprimée en format étendu au lieu d'un format à 4 chiffres. Pour plus d’informations, consultez [Années étendues](../javascript/date-and-time-strings-javascript.md#bkmk_extend) plus loin dans cette rubrique.||  
|`MM`|Mois|01 à 12|  
|`DD`|Jour du mois|01 à 31|  
|`HH`|Heures|00 à 24|  
|`mm`|Minutes|00 à 59|  
|`ss`|Secondes. Les secondes et les millisecondes sont facultatives si une heure est spécifiée.|00 à 59|  
|`sss`|Millisecondes|00 à 999|  
|`Z`|À cet emplacement, la valeur peut être l'une des suivantes : Si la valeur est omise, le format UTC est utilisé.<br /><br /> -   `Z` indique l’heure UTC.<br />-   `+hh:mm` indique que l’heure en entrée est le décalage spécifié après l’heure UTC.<br />-   `-hh:mm` indique que l’heure en entrée est la valeur absolue du décalage spécifié avant l’heure UTC.||  
  
 La chaîne peut inclure uniquement la date, comme dans les formats suivants : `YYYY`, `YYYY-MM`, `YYYY-MM-DD`.  
  
 Les noms de fuseau horaire ne sont pas pris en charge par le format ISO. Utilisez la position `Z` pour spécifier un décalage à partir de l'heure UTC. Si vous n'incluez pas de valeur dans la position `Z`, l'heure UTC est utilisée.  
  
 Minuit peut être spécifié sous la forme 0:00, ou sous la forme 24:00 (dans ce cas, il s'agit de la veille). Les deux chaînes suivantes spécifient la même heure : 2010-05-25T00:00 et 2010-05-24T24:00.  
  
 Pour retourner une date au format ISO, vous pouvez utiliser la méthode [toISOString (Date)](../javascript/reference/toisostring-method-date-javascript.md).  
  
<a name="bkmk_extend"></a>   
### <a name="extended-years"></a>Années étendues  
 Une *année étendue* comporte six chiffres au lieu de quatre et est précédée du signe plus ou moins. Exemple d'une année étendue : `+002010`, qui équivaut à `2010`. Une année étendue peut être utilisée pour représenter les années avant l'année 0 ou après l'année 9999.  
  
 Si vous utilisez le format à 6 chiffres, la présence du signe plus ou moins est requise. Lorsque vous utilisez le format à 4 chiffres, l'absence du signe est requise. Par conséquent, `0000` et `+000000` sont acceptés, mais `000000` et `-0001` provoquent une erreur. L'année étendue 0 est considérée comme étant une valeur positive. Elle est donc précédée du signe plus.  
  
 La méthode [toISOString (Date)](../javascript/reference/toisostring-method-date-javascript.md) utilise toujours le format étendu pour les années antérieures à l’année 0 et celles postérieures à l’année 9999.  
  
> [!NOTE]
>  [!INCLUDE[jsv9](../javascript/includes/jsv9-md.md)]  
  
<a name="OtherDateFormats"></a>   
## <a name="other-date-formats"></a>Autres formats de date  
 Si une chaîne de date n'est pas au format ISO, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] utilise les règles suivantes pour l'analyser.  
  
 Dates courtes  
  
-   Le format doit respecter l'ordre suivant : jour/mois/année, par exemple « 08/06/2010 ».  
  
-   « / » ou « - » peuvent être utilisés comme séparateurs.  
  
 Dates longues  
  
-   L'année, le mois et le jour peuvent se présenter dans n'importe quel ordre. « 8 juin 2010 » et « 08/06/2010 » sont valides tous les deux.  
  
-   L'année peut comporter deux ou quatre chiffres. Si l'année comporte deux chiffres, elle doit avoir au moins la valeur 70.  
  
-   Les noms de mois et de jour doivent avoir au moins deux caractères. Pour les noms à deux caractères qui ne sont pas uniques, le dernier nom correspondant est reconnu. Par exemple, « Ju » spécifie juillet, et non juin.  
  
-   Un jour de la semaine est ignoré s'il est incohérent avec le reste de la date fournie. Par exemple, « mardi 9 novembre 1996 » est résolu en « vendredi 9 novembre 1996 », car vendredi est le jour de la semaine approprié pour cette date.  
  
 Heures  
  
-   Les heures, les minutes et les secondes sont séparées par deux-points. Toutefois, certaines parties peuvent être omises. Les valeurs suivantes sont valides : « 10: », « 10:11 » et « 10:11:12 ».  
  
-   Si PM est indiqué et que l'heure spécifiée est au moins égale à 13, NaN est retourné. Par exemple, « 23:15 PM » retourne NaN.  
  
 Général  
  
-   Une chaîne contenant une date non valide retourne NaN. Par exemple, une chaîne qui contient deux années ou deux mois retourne NaN.  
  
-   [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] prend en charge les fuseaux horaires standards, le temps universel (UTC) et l'heure de Greenwich (GMT). (Les noms du fuseau horaire ne sont pas pris en charge par le format ISO.)  
  
-   Le texte entre parenthèses est traité comme commentaire. Les parenthèses peuvent être imbriquées.  
  
-   Les virgules et les espaces sont traités comme délimiteurs. Plusieurs délimiteurs sont autorisés.  
  
## <a name="example"></a>Exemple  
 Le code suivant affiche les résultats d'analyse de différentes chaînes de date et d'heure.  
  
```  
document.writeln((new Date("2010")).toUTCString());   
  
document.writeln((new Date("2010-06")).toUTCString());  
  
document.writeln((new Date("2010-06-09")).toUTCString());  
  
 // Specifies Z, which indicates UTC time.  
document.writeln((new Date("2010-06-09T15:20:00Z")).toUTCString());  
  
 // Specifies -07:00 offset, which is equivalent to Pacific Daylight time.  
document.writeln((new Date("2010-06-09T15:20:00-07:00")).toGMTString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("June 9, 2010")).toUTCString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("2010 June 9")).toUTCString());  
  
// Specifies a non-ISO Short date and time.  
document.writeln((new Date("6/9/2010 3:20 pm")).toUTCString());  
  
// Output:  
// Fri, 1 Jan 2010 00:00:00 UTC  
// Tue, 1 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 15:20:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
```  
  
 Lorsque les heures locales sont spécifiées, le résultat varie selon le fuseau horaire.  
  
> [!IMPORTANT]
>  Le format de date ISO n'est pris en charge ni par Internet Explorer 8 (mode normes) ni par le mode Quirks.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Date](../javascript/reference/date-object-javascript.md)   
 [Fonction Date.parse](../javascript/reference/date-parse-function-javascript.md)