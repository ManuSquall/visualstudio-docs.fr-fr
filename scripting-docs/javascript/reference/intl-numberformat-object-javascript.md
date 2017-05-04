---
title: "Intl.NumberFormat, objet (JavaScript) | Microsoft Docs"
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
  - "NumberFormat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Intl.NumberFormat, objet (JavaScript)
Fournit la mise en forme spécifique aux paramètres régionaux de nombre.  
  
## Syntaxe  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### Paramètres  
 `numberFormatObj`  
 Requis.  Nom de variable à attribuer à l'objet `NumberFormat`.  
  
 `locales`  
 Optionnel.  Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux.  Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez\-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut.  Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés.  Pour plus d'informations, consultez la section Notes.  
  
 `options`  
 Optionnel.  Un objet qui contient une ou plusieurs propriétés qui spécifient les options de mise en forme des nombres.  Pour plus d'informations, consultez la section Notes.  
  
## Notes  
 Le paramètre `locales` doit respecter les balises de langue ou de paramètres régionaux [BCP 47](http://tools.ietf.org/html/rfc5646) telles que « en\-US » et « zh\-CN ».  La balise peut inclure la langue, la région, le pays et la variante.  Pour obtenir des exemples de balises de langue, consultez [Annexe A](http://tools.ietf.org/html/rfc5646#appendix-A) de BCP 47.  Pour `NumberFormat`, vous pouvez ajouter la sous\-balise **\-u** suivie par \-nu pour spécifier une extension du système de numérotation :  
  
 "*language*\-*region*\-u\-le NU\-*numberingsystem*"  
  
 où *numberingsystem* peut être l'une des valeurs suivantes : arabe, arabext, bali, beng, deva, fullwide, gujr, guru, hanidec, khmr, knda, laoo, latn, limb, mylm, mong, mymr, orya, tamldec, telu, thaï, tibt.  
  
 Le paramètre `options` peut inclure les propriétés suivantes :  
  
|Propriété|Description|Valeurs possibles|Valeur par défaut|  
|---------------|-----------------|-----------------------|-----------------------|  
|`localeMatcher`|Spécifie l'algorithme de correspondance aux paramètres régionaux à utiliser.|« rechercher », « ajustement optimal »|« ajustement optimal »|  
|`style`|Spécifie le style de format numérique.|« décimal », « pour cent », « devise »|« decimal »|  
|`currency`|Spécifie la valeur monétaire ISO 4217 comme code alphabétique.  Si `style` a la valeur « monnaie », cette valeur est requise.|Consultez la [liste des codes de devises et des fonds ISO](http://www.currency-iso.org/en/home/tables/table-a1.html).|indéfini|  
|`currencyDisplay`|Spécifie si la monnaie doit être affichée comme un code de devise alphabétique ISO 4217, un symbole monétaire localisé ou un nom de devise localisé.  Cette valeur est utilisée uniquement lorsque `style` est défini sur "currency".|« code », « symbole », « nom »|"symbol"|  
|`useGrouping`|Spécifie si un séparateur de regroupement doit être utilisé.|true, false|`true`.|  
|`minimumIntegerDigits`|Spécifie le nombre minimal de chiffres intégraux à utiliser.|1 à 21.|21|  
|`minimumFractionDigits`|.  Spécifie le nombre minimal de chiffres fractionnaires à utiliser.|0 à 20.|0|  
|`maximumFractionDigits`|Spécifie le nombre maximal de chiffres fractionnaires à utiliser.|Cette valeur peut varier de `minimumFractionDigits` à 20.|20.|  
|`minimumSignificantDigits`|Spécifie le nombre minimal de chiffres fractionnaires à afficher.|Cette valeur peut varier de 1 à 21.|1|  
|`maximumSignificantDigits`|Spécifie le nombre maximal de chiffres fractionnaires à afficher.|Cette valeur peut varier de `minimumSignificantDigits` à 21.|21|  
  
## Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `NumberFormat`.  
  
|||  
|-|-|  
|Propriété|Description|  
|[Constructeur](../../javascript/reference/constructor-property-intl-numberformat.md)|Spécifie la fonction qui crée un objet formateur de nombre.|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|Retourne une fonction qui met un nombre en forme à l'aide des paramètres du formateur de nombres.|  
|[prototype](../../javascript/reference/prototype-property-intl-numberformat.md)|Retourne une référence au prototype d'un formateur numérique.|  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `NumberFormat`.  
  
|||  
|-|-|  
|Méthode|Description|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|Retourne un objet qui contient des propriétés et des valeurs de l'objet formateur de nombre.|  
  
## Exemple  
 L'exemple suivant crée un objet `NumberFormat` pour les paramètres régionaux américains à l'aide des options de mise en forme spécifiées.  
  
```javascript  
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
  
## Exemple  
 Les exemples suivants montrent le résultat de l'utilisation de plusieurs options et paramètres régionaux différents.  
  
```javascript  
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
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Voir aussi  
 [toLocaleString \(Number\)](../../javascript/reference/tolocalestring-number.md)   
 [Intl.Collator, objet](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.DateTimeFormat, objet](../../javascript/reference/intl-datetimeformat-object-javascript.md)