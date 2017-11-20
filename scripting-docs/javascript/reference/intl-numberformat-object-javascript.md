---
title: Intl.NumberFormat, objet (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: NumberFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dcb02dbe0d7a7eef88750c440a4fbcdde3ea7ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="intlnumberformat-object-javascript"></a>Intl.NumberFormat, objet (JavaScript)
Fournit la mise en forme de nombre spécifique aux paramètres régionaux.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Paramètres  
 `numberFormatObj`  
 Obligatoire. Nom de variable à attribuer à l'objet `NumberFormat`.  
  
 `locales`  
 Facultatif. Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux. Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut. Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés. Pour plus d'informations, consultez la section Notes.  
  
 `options`  
 Facultatif. Objet qui contient une ou plusieurs propriétés qui spécifient les options de mise en forme de nombre. Pour plus d'informations, consultez la section Notes.  
  
## <a name="remarks"></a>Remarques  
 Le `locales` paramètre doit être conformes aux [BCP 47](http://tools.ietf.org/html/rfc5646) balises de langue ou paramètres régionaux telles que « en-US » et « zh-CN ». L’étiquette peut inclure la langue, la région, le pays et la variante. Pour obtenir des exemples de balises de langue, consultez [annexe A](http://tools.ietf.org/html/rfc5646#appendix-A) BCP 47. Pour `NumberFormat`, vous pouvez ajouter la **-u** sous-balise suivie - nu pour spécifier une extension de système de numérotation :  
  
 «*langage*-*région*-u-nu -*numberingsystem*»  
  
 où *numberingsystem* peut être une des valeurs suivantes : arabe, arabext, bali, beng, deva, fullwide, gujr, expert, hanidec, khmr, knda, laoo, latn, un membre, mylm, ja mais navigué, mymr, orya, tamldec, telu, thaï, tibt.  
  
 Le paramètre `options` peut inclure les propriétés suivantes :  
  
|Propriété|Description|Valeurs possibles |Valeur par défaut|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Spécifie l'algorithme de correspondance avec les paramètres régionaux à utiliser.|« Rechercher », « ajustement optimal »|« ajustement optimal »|  
|`style`|Spécifie le style de format de nombre.|« décimal », « pourcentage », « devise »|« décimal »|  
|`currency`|Spécifie la valeur de devise ISO 4217 comme un code alphabétique. Si le `style` a la valeur « devise », cette valeur est obligatoire.|Consultez le fichier ISO [liste de code de devise et fonds](http://www.currency-iso.org/en/home/tables/table-a1.html).|non défini|  
|`currencyDisplay`|Spécifie s’il faut afficher la devise comme un code de devise alphabétique ISO 4217, un symbole monétaire localisé ou un nom localisé de devise. Cette valeur est utilisée uniquement si `style` a la valeur « devise ».|« code », « symboles », « name »|« symbole »|  
|`useGrouping`|Spécifie si un séparateur de regroupement doit être utilisé.|la valeur est true, false|`true`.|  
|`minimumIntegerDigits`|Spécifie le nombre minimal de chiffres intégraux à utiliser.|1 à 21.|21|  
|`minimumFractionDigits`|. Spécifie le nombre minimal de chiffres fractionnaires à utiliser.|0 à 20.|0|  
|`maximumFractionDigits`|Spécifie le nombre maximal de chiffres fractionnaires à utiliser.|Cette valeur peut varier de `minimumFractionDigits` à 20.|20.|  
|`minimumSignificantDigits`|Spécifie le nombre minimal de chiffres fractionnaires à afficher.|Cette valeur peut varier de 1 à 21.|1|  
|`maximumSignificantDigits`|Spécifie le nombre maximal de chiffres fractionnaires à afficher.|Cette valeur peut varier de `minimumSignificantDigits` sur 21.|21|  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `NumberFormat`.  
  
|||  
|-|-|  
|Propriété|Description|  
|[constructeur](../../javascript/reference/constructor-property-intl-numberformat.md)|Spécifie la fonction qui crée un objet de module de formatage de nombre.|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|Retourne une fonction qui met en forme un nombre en utilisant les paramètres de module de formatage de nombre.|  
|[prototype](../../javascript/reference/prototype-property-intl-numberformat.md)|Retourne une référence au prototype pour un module de formatage de nombre.|  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `NumberFormat`.  
  
|||  
|-|-|  
|Méthode|Description|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|Retourne un objet qui contient les propriétés et valeurs de l’objet formateur number.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un `NumberFormat` objet des paramètres régionaux en-US avec les options de mise en forme spécifiées.  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent le résultat de l’utilisation de plusieurs options et paramètres régionaux différents.  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [toLocaleString (nombre)](../../javascript/reference/tolocalestring-number.md)   
 [Intl.Collator, objet](../../javascript/reference/intl-collator-object-javascript.md)   
 [Objet Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)