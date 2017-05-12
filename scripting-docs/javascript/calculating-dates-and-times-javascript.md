---
title: "Calcul des dates et des heures (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "arithmétique de date et d'heure (JavaScript)"
  - "JavaScript, date et heure"
  - "comparaison de dates (JavaScript)"
  - "calculs de date et d'heure (JavaScript)"
ms.assetid: ea976f78-d934-479b-9056-880390d8bddd
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# Calcul des dates et des heures (JavaScript)
Vous pouvez utiliser l'[objet Date](../javascript/reference/date-object-javascript.md) pour effectuer des tâches courantes de calendrier et d'horloge, telles que la comparaison de dates et le calcul du temps écoulé.  
  
## Définition d'une date à la date actuelle  
 Lorsque vous créez une instance de l'[objet Date](../javascript/reference/date-object-javascript.md) sans spécifier de date, il retourne une valeur représentant la date et l'heure actuelles, y compris l'année, le mois, le jour, l'heure, la minute, la seconde et la milliseconde.  Vous pouvez alors lire ou modifier cette date et heure.  
  
 L'exemple suivant montre comment instancier une date sans utiliser aucun paramètre et l'afficher au format *mm\-dd\-yy*.  
  
```javascript  
var dt = new Date();  
  
// Display the month, day, and year. getMonth() returns a 0-based number.  
var month = dt.getMonth()+1;  
var day = dt.getDate();  
var year = dt.getFullYear();  
document.write(month + '-' + day + '-' + year);  
  
// Output: current month, day, year  
```  
  
## Définition d'une date spécifique  
 Vous pouvez définir une date spécifique en passant une chaîne de date au constructeur.  
  
```javascript  
var dt = new Date('8/24/2009');  
document.write(dt);  
  
// Output: Mon Aug 24 00:00:00 PDT 2009  
  
```  
  
> [!IMPORTANT]
>  Le fuseau horaire affiché dans la chaîne de date correspond au fuseau horaire défini sur l'ordinateur local.  
>   
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] est flexible sur le format de la chaîne que vous utilisez comme paramètre.  Par exemple, vous pouvez entrer « 24\-08\-2009 », « 24\/08\/2009 » ou « 24 août 2009 ».  
  
 Vous pouvez également spécifier une heure.  L'exemple suivant montre une façon de spécifier une date et une heure au format ISO.  Le « Z » indique l'heure UTC.  
  
```javascript  
var dt = new Date('2010-06-09T15:20:00Z');  
document.write(dt);  
document.write("<br />");  
document.write(dt.toISOString());  
  
// Output:  
// Wed Jun 09 2010 08:20:00 GMT-0700 (Pacific Daylight Time)  
// 2010-06-09T15:20:00.000Z  
```  
  
 Pour plus d'informations sur les formats de date, comme ISO, consultez [Chaînes de date et heure](../javascript/date-and-time-strings-javascript.md).  
  
 L'exemple suivant montre d'autres façons de spécifier une heure.  
  
```javascript  
var dtA = new Date('8/24/2009 14:52:10');  
  
// The parameters are year, month, day, hours, minutes, seconds.  
var dtB = new Date(2009, 7, 24, 14, 52, 10);  
document.write(dtA);  
document.write("<br/>");  
document.write(dtB);  
  
// Output:  
// Mon Aug 24 14:52:10 PDT 2009  
// Mon Aug 24 14:52:10 PDT 2009  
  
```  
  
## Ajout et soustraction des jours, des mois et des années  
 Vous pouvez utiliser les méthodes getX et setX de l'objet `Date` pour définir des dates et des heures spécifiques.  
  
 L'exemple suivant montre comment définir une date à celle du jour précédent.  Notez que, si nécessaire, les valeurs mois et année sont également modifiées.  
  
```javascript  
var myDate = new Date("1/1/1990");  
var dayOfMonth = myDate.getDate();  
myDate.setDate(dayOfMonth - 1);  
  
document.write(myDate);  
  
// Output: Sun Dec 31 00:00:00 PST 1989  
```  
  
 L'exemple suivant définit la date au dernier jour du mois en soustrayant un jour à partir du premier jour du mois suivant.  
  
> [!TIP]
>  Les mois de l'année sont numérotés de 0 \(janvier\) à 11 \(décembre\).  Les jours de la semaine sont numérotés de 0 \(dimanche\) à 6 \(samedi\).  
  
```javascript  
var myDate = new Date("1/1/1990")  
myDate.setMonth(myDate.getMonth() + 1);  
  
myDate.setDate (myDate.getDate() - 1);  
  
document.write(myDate);  
  
// Output: Wed Jan 31 00:00:00 PST 1990  
  
```  
  
## Utilisation des jours de la semaine  
 La [méthode getDay](../javascript/reference/getday-method-date-javascript.md) obtient le jour de la semaine en tant que nombre compris entre 0 \(dimanche\) et 6 \(samedi\). \(Elle est différente de la [méthode getDate](../javascript/reference/getdate-method-date-javascript.md), qui obtient le jour du mois sous forme d'un nombre compris entre 1 et 31\).  
  
 L'exemple suivant définit la date du jour de Thanksgiving, qui est défini aux États\-Unis comme étant le quatrième jeudi du mois de novembre.  Le script recherche le 1er novembre de l'année actuelle, détermine le premier jeudi, puis ajoute trois semaines.  
  
```javascript  
var myDate = new Date();  
myDate.setHours(0, 0, 0, 0);  
  
myDate.setYear(2013);  
  
// Determine November 1.  
myDate.setDate(1);  
myDate.setMonth(10);  
  
// Find Thursday.  
var thursday = 4;  
while(myDate.getDay() != thursday) {  
    myDate.setDate(myDate.getDate() + 1);  
}  
  
// Add 3 weeks.  
myDate.setDate(myDate.getDate() + 21);  
  
document.write(myDate);  
  
// Output: Thu Nov 28 00:00:00 <time zone> 2013  
  
```  
  
## Calcul du temps écoulé  
 La [méthode getTime](../javascript/reference/gettime-method-date-javascript.md) retourne le nombre de millisecondes qui se sont écoulées depuis le 1er janvier 1970 à minuit.  Pour toute date antérieure, elle retourne un nombre négatif.  
  
 Vous pouvez utiliser la [méthode getTime](../javascript/reference/gettime-method-date-javascript.md) pour définir une heure de début et de fin lors du calcul d'un temps écoulé.  Il peut être utilisé pour mesurer de petites unités \(telles que des secondes\) et grandes unités \(telles que des jours\).  
  
 L'exemple suivant calcule le temps écoulé en secondes.  La [méthode getTime](../javascript/reference/gettime-method-date-javascript.md) obtient le nombre de millisecondes depuis la date zéro.  
  
```javascript  
var startTime = new Date('1/1/1990');  
var startMsec = startTime.getMilliseconds();  
startTime.setTime(5000000);  
var elapsed = (startTime.getTime() - startMsec) / 1000;   
document.write(elapsed);  
  
// Output: 5000  
  
```  
  
 Pour utiliser des unités plus pratiques, vous pouvez diviser les millisecondes fournies par la [méthode getTime](../javascript/reference/gettime-method-date-javascript.md) par un nombre approprié.  Par exemple, pour convertir des millisecondes en jours, divisez le nombre par 86 400 000 \(1000 millisecondes x 60 minutes x 24 heures\).  
  
 L'exemple suivant indique le temps qui s'est écoulé depuis le premier jour de l'année spécifiée.  Il utilise des opérations de division pour calculer le temps écoulé en jours, heures, minutes et secondes.  Il ne tient pas compte de l'heure d'été.  
  
```javascript  
// Set the unit values in milliseconds.  
var msecPerMinute = 1000 * 60;  
var msecPerHour = msecPerMinute * 60;  
var msecPerDay = msecPerHour * 24;  
  
// Set a date and get the milliseconds  
var date = new Date('6/15/1990');  
var dateMsec = date.getTime();  
  
// Set the date to January 1, at midnight, of the specified year.  
date.setMonth(0);  
date.setDate(1);  
date.setHours(0, 0, 0, 0);  
  
// Get the difference in milliseconds.  
var interval = dateMsec - date.getTime();  
  
// Calculate how many days the interval contains. Subtract that  
// many days from the interval to determine the remainder.  
var days = Math.floor(interval / msecPerDay );  
interval = interval - (days * msecPerDay );  
  
// Calculate the hours, minutes, and seconds.  
var hours = Math.floor(interval / msecPerHour );  
interval = interval - (hours * msecPerHour );  
  
var minutes = Math.floor(interval / msecPerMinute );  
interval = interval - (minutes * msecPerMinute );  
  
var seconds = Math.floor(interval / 1000 );  
  
// Display the result.  
document.write(days + " days, " + hours + " hours, " + minutes + " minutes, " + seconds + " seconds.");  
  
//Output: 164 days, 23 hours, 0 minutes, 0 seconds.  
```  
  
### Détermination de l'âge de l'utilisateur  
 L'exemple suivant utilise l'anniversaire de l'utilisateur et calcule l'âge de l'utilisateur en années.  Il soustrait l'année de naissance de l'année actuelle, puis soustrait 1 si la date d'anniversaire n'a pas été dépassée dans l'année en cours.  
  
```javascript  
var birthday = new Date("8/1/1985");  
var today = new Date();  
var years = today.getFullYear() - birthday.getFullYear();  
  
// Reset birthday to the current year.  
birthday.setFullYear(today.getFullYear());  
  
// If the user's birthday has not occurred yet this year, subtract 1.  
if (today < birthday)  
{  
    years--;  
}  
document.write("You are " + years + " years old.");  
  
// Output: You are <number of years> years old.  
  
```  
  
## Comparaison de dates  
 Lorsque vous comparez des dates dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], vous devez garder à l'esprit que l'opérateur `==` retourne `true` uniquement si les dates des deux côtés de l'opérateur font référence au même objet.  Par conséquent, si vous définissez deux objets `Date` distincts à la même date, `date1 == date2` retourne `false`.  De plus, un objet `Date` défini avec uniquement la date mais pas l'heure, est initialisé à cette même date à minuit.  Si vous comparez une `Date` définie sans heure spécifique avec le paramètre `Date.now`, par exemple, vous devez savoir que la première `Date` est définie à minuit et que le paramètre `Date.now` ne l'est pas.  
  
 L'exemple suivant vérifie si la date actuelle est la même qu'une date spécifiée, ou si elle est antérieure ou postérieure.  Pour définir la date actuelle dans `todayAtMidn`, le script crée un objet `Date` pour l'année, le mois et le jour actuels.  
  
```javascript  
// Get the current date at midnight.  
var now = new Date();   
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set specificDate to a specified date at midnight.  
var specificDate = new Date("9/21/2009");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() == specificDate.getTime())  
{  
    document.write("Same");  
}  
else  
{  
    document.write("Different");  
}  
  
//Output: Different  
```  
  
 En modifiant l'exemple précédent, nous pouvons vérifier si une date fournie appartient à une plage spécifique.  
  
```javascript  
// Get the current date at midnight.  
var now = new Date();  
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set start/end dates to a specified date (ISO format).  
var startDate = new Date("2009-06-09T15:20:00Z");  
var endDate = new Date("2011-06-09T15:20:00Z");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() > startDate.getTime() &&   
    todayAtMidn.getTime() < endDate.getTime()) {  
    document.write("Specified date is within this range.");  
}  
else {  
    document.write("Specified date is not in this range.");  
}  
  
// Output: Specified date is not in this range.  
```  
  
## Voir aussi  
 [Date, objet](../javascript/reference/date-object-javascript.md)