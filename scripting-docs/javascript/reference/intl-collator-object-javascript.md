---
title: "Intl.Collator, objet (JavaScript) | Microsoft Docs"
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
  - "Collator"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Intl.Collator, objet (JavaScript)
Fournit des comparaisons de chaînes spécifiques aux paramètres régionaux.  
  
## Syntaxe  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### Paramètres  
 `collatorObj`  
 Requis.  Nom de variable à attribuer à l'objet `Collator`.  
  
 `locales`  
 Optionnel.  Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux.  Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez\-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut.  Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés.  Pour plus d'informations, consultez la section Notes.  
  
 `options`  
 Optionnel.  Objet qui contient une ou plusieurs propriétés qui spécifient les options de comparaison.  Pour plus d'informations, consultez la section Notes.  
  
## Notes  
 Le paramètre `locales` doit respecter les balises de langue ou de paramètres régionaux [BCP 47](http://tools.ietf.org/html/rfc5646) telles que « en\-US » et « zh\-Hans\-CN ».  La balise peut inclure la langue, la région, le pays et la variante.  Pour une liste des langues, consultez le [registre de sous\-balises de langage IANA](http://go.microsoft.com/fwlink/p/?linkid=227303).  Pour obtenir des exemples de balises de langue, consultez [Annexe A](http://tools.ietf.org/html/rfc5646#appendix-A) de BCP 47.  Pour `Collator`, vous pouvez inclure l'extension \-u à la chaîne de paramètres régionaux pour spécifier une ou plusieurs des extensions Unicode suivantes :  
  
-   \-co pour spécifier les classements variants \(spécifiques aux paramètres régionaux\) : "*language*\-*region*\-u\-co\-*value*".  
  
-   \-kn pour spécifier une comparaison numérique : "*language*\-*region*\-u\-kn\-true&#124;false".  
  
-   –kf pour spécifier s'il s'agit d'un tri par majuscules ou minuscules en premier : "*language*\-*region*\-u\-kf\-upper&#124;lower&#124;false"\).  Cette extension n'est actuellement pas prise en charge.  
  
 Pour spécifier une comparaison numérique, vous pouvez définir l'extension –kn dans la chaîne de paramètres régionaux ou utiliser la propriété `numeric` du paramètre `options`.  Si vous utilisez la propriété `numeric`, la valeur –kn ne s'appliquera pas.  
  
 Le paramètre `options` peut inclure les propriétés suivantes :  
  
-   `localeMatcher`.  Spécifie l'algorithme de correspondance aux paramètres régionaux à utiliser.  Les valeurs possibles sont « lookup » et « best fit ».  La valeur par défaut est "best fit".  
  
-   `usage`.  Spécifie si l'objectif de la comparaison est le tri ou la recherche.  Les valeurs possibles sont « sort » et « search ».  La valeur par défaut est "sort".  
  
-   `sensitivity`.  Spécifie le critère de sensibilité de l'assembleur.  Les valeurs possibles sont « base », « accent », « case » et « variant ».  La valeur par défaut est `undefined`.  
  
-   `ignorePunctuation`.  Spécifie si la ponctuation est ignorée dans la comparaison.  Les seules valeurs valides sont 'true' et 'false'.  La valeur par défaut est `false`.  
  
-   `numeric`.  Spécifie si le tri numérique est utilisé.  Les seules valeurs valides sont 'true' et 'false'.  La valeur par défaut est `false`.  
  
-   `caseFirst`.  Non pris en charge actuellement.  
  
## Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Collator`.  
  
|||  
|-|-|  
|Propriété|Description|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|Retourne une fonction qui compare deux chaînes à l'aide de l'ordre de tri de l'assembleur.|  
|[Constructeur](../../javascript/reference/constructor-property-intl-collator.md)|Spécifie la fonction qui crée un objet assembleur.|  
|[prototype](../../javascript/reference/prototype-property-intl-collator.md)|Retourne une référence au prototype d'un assembleur.|  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Collator`.  
  
|||  
|-|-|  
|Méthode|Description|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|Retourne un objet contenant des propriétés et des valeurs de l'assembleur.|  
  
## Exemple  
 L'exemple suivant crée un objet `Collator` et effectue une comparaison.  
  
```javascript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## Exemple  
 L'exemple suivant utilise des objets `Collator` pour trier un tableau.  Cet exemple illustre les différences spécifiques aux paramètres régionaux.  
  
```javascript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## Exemple  
 L'exemple suivant utilise un objet `Collator` pour rechercher une chaîne et spécifie les options de comparaison.  
  
```javascript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Voir aussi  
 [localeCompare, méthode \(String\)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Intl.DateTimeFormat, objet](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Intl.NumberFormat, objet](../../javascript/reference/intl-numberformat-object-javascript.md)