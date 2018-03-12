---
title: Intl.DateTimeFormat, objet (JavaScript) | Documents Microsoft
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
- DateTimeFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: cc555ac2-f31c-4239-a612-b84c08e3a37f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c50d6d7d939ebe05ce3ff9b434111413803ea40
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="intldatetimeformat-object-javascript"></a>Intl.DateTimeFormat, objet (JavaScript)
Fournit la mise en forme spécifique aux paramètres régionaux de date et d'heure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
dateTimeFormatObj = new Intl.DateTimeFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dateTimeFormatObj`  
 Obligatoire. Nom de variable à attribuer à l'objet `DateTimeFormat`.  
  
 `locales`  
 Facultatif. Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux. Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut. Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés. Pour plus d'informations, consultez la section Notes.  
  
 `options`  
 Facultatif. Objet qui contient une ou plusieurs propriétés spécifiant les options de mise en forme de date et d'heure. Pour plus d'informations, consultez la section Notes.  
  
## <a name="remarks"></a>Remarques  
 Le `locales` paramètre doit être conformes aux [BCP 47](http://tools.ietf.org/html/rfc5646) balises de langue ou paramètres régionaux telles que « en-US » et « zh-CN ». L’étiquette peut inclure la langue, la région, le pays et la variante. Pour obtenir des exemples de balises de langue, consultez [annexe A](http://tools.ietf.org/html/rfc5646#appendix-A) BCP 47. Pour `DateTimeFormat`, vous pouvez ajouter la **-u** sous-balise dans la chaîne de paramètres régionaux pour inclure une ou les deux extensions Unicode suivantes :  
  
-   -nu pour spécifier une extension de système de numérotation : *langage*-*région*-u-nu -*numberingsystem*  
  
     où *numberingsystem* peut être une des valeurs suivantes : arabe, arabext, bali, beng, deva, fullwide, gujr, expert, hanidec, khmr, knda, laoo, latn, un membre, mylm, ja mais navigué, mymr, orya, tamldec, telu, thaï, tibt.  
  
-   -ca pour spécifier un calendrier : *langage*-*région*-u-AC -*calendrier*  
  
     où *calendrier* peut être un des éléments suivants : bouddhiste, chinois, gregory, islamique, islamicc, japonais.  
  
 Le paramètre `options` peut inclure les propriétés suivantes :  
  
|Propriété|Description|Valeurs possibles |Valeur par défaut|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Spécifie l'algorithme de correspondance avec les paramètres régionaux à utiliser.|« rechercher », « ajustement optimal »|« ajustement optimal »|  
|`formatMatcher`|Spécifie l'algorithme de correspondance avec le format à utiliser.|« basique », « ajustement optimal »|« ajustement optimal »|  
|`hour12`|Spécifie s'il faut utiliser un format de 12 heures pour les heures.|`true` (pour le format 12 heures), `false` (pour le format 24 heures)||  
|`timeZone`|Spécifie le fuseau horaire. Au minimum, « UTC » est toujours pris en charge.|Valeur de fuseau horaire telle que « UTC ».|« UTC » (temps universel coordonné)|  
|`weekday`|Spécifie la mise en forme du jour de la semaine.|« étroit », « court », « long ».|non défini|  
|`era`|Spécifie la mise en forme de l'ère.|« étroit », « court », « long »|non défini|  
|`year`|Spécifie la mise en forme de l'année.|« 2 chiffres », « numérique »|non défini ou « numérique »|  
|`month`|Spécifie la mise en forme du mois.|« 2 chiffres », « numérique », « étroit », « court », « long »|non défini ou « numérique »|  
|`day`|Spécifie la mise en forme du jour.|« 2 chiffres », « numérique »|non défini ou « numérique »|  
|`hour`|Spécifie la mise en forme de l'heure.|« 2 chiffres », « numérique »|non défini|  
|`minute`|Spécifie la mise en forme de la minute.|« 2 chiffres », « numérique »|non défini|  
|`second`|Spécifie la mise en forme de la seconde.|« 2 chiffres », « numérique »|non défini|  
|`timeZoneName`|Spécifie la mise en forme du fuseau horaire. Cette propriété n'est pas prise en charge actuellement.|« court », « long ».|Cette propriété n'est pas prise en charge actuellement.|  
  
 Les valeurs par défaut pour `weekday`, `era`, `year`, `month`, `day`, `hour`, `minute` et `second` sont `undefined`. Si vous ne définissez pas ces propriétés, la mise en forme « numérique » est utilisée pour `year`, `month` et `day`.  
  
 Chaque paramètre régional doit prendre en charge, au minimum, les formats suivants :  
  
-   jour de la semaine, année, mois, jour, heure, minute, seconde  
  
-   jour de la semaine, année, mois, jour  
  
-   année, mois, jour  
  
-   année, mois  
  
-   mois, jour  
  
-   heure, minute, seconde  
  
-   heure, minute  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `DateTimeFormat`.  
  
|||  
|-|-|  
|Propriété|Description|  
|[constructeur](../../javascript/reference/constructor-property-intl-datetimeformat.md)|Spécifie la fonction qui crée un formateur de date/heure.|  
|[format](../../javascript/reference/format-property-intl-datetimeformat.md)|Retourne une fonction qui met en forme une date spécifique aux paramètres régionaux à l'aide des paramètres du formateur de date/heure.|  
|[prototype](../../javascript/reference/prototype-property-intl-datetimeformat.md)|Retourne une référence au prototype pour un formateur de date/heure.|  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `DateTimeFormat`.  
  
|||  
|-|-|  
|Méthode|Description|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-datetimeformat.md)|Retourne un objet qui contient les propriétés et les valeurs de l'objet formateur de date/heure.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant affiche le résultat du passage d'un objet date à `DateTimeFormat` en utilisant différents paramètres régionaux.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
if (console && console.log) {  
    console.log(new Intl.DateTimeFormat("en-US").format(date));  
    // Returns ‎2‎/‎1‎/‎2013  
    console.log(new Intl.DateTimeFormat("ja-JP").format(date));  
    // Returns ‎2013‎年‎2‎月‎1‎日  
    console.log(new Intl.DateTimeFormat("ar-SA", options).format(date));  
    // Returns ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
    console.log(new Intl.DateTimeFormat("hi-IN", options).format(date));  
    // Returns ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
}  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée un objet `DateTimeFormat` qui spécifie le jour de la semaine actuel au format long en utilisant les paramètres régionaux arabes (Arabie Saoudite), le calendrier islamique et le système de numérotation latin.  
  
```JavaScript  
var dtf = new Intl.DateTimeFormat(["ar-SA-u-ca-islamic-nu-latn"], {  
    weekday: "long",  
    year: "numeric",  
    day: "numeric",  
    month: "long"  
});   
  
If (console && console.log) {  
    console.log(dtf.format(new Date()));  
    // Returns ‏الجمعة‏, ‏19‏ ‏رمضان‏, ‏1434  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [toLocaleString (Date)](../../javascript/reference/tolocalestring-date.md)   
 [toLocaleDateString, méthode (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)   
 [toLocaleTimeString, méthode (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)   
 [Intl.Collator, objet](../../javascript/reference/intl-collator-object-javascript.md)   
 [Objet Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)