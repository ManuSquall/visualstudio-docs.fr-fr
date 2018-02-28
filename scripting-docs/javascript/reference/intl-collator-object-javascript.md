---
title: Intl.Collator, objet (JavaScript) | Documents Microsoft
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
- Collator
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9a41507face20285124257be95197ef5ea53ef6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="intlcollator-object-javascript"></a>Intl.Collator, objet (JavaScript)
Permet des comparaisons de chaînes spécifiques aux paramètres régionaux.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### <a name="parameters"></a>Paramètres  
 `collatorObj`  
 Obligatoire. Nom de variable à attribuer à l'objet `Collator`.  
  
 `locales`  
 Facultatif. Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux. Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut. Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés. Pour plus d'informations, consultez la section Notes.  
  
 `options`  
 Facultatif. Objet qui contient une ou plusieurs propriétés qui spécifient des options de comparaison. Pour plus d'informations, consultez la section Notes.  
  
## <a name="remarks"></a>Remarques  
 Le `locales` paramètre doit être conformes aux [BCP 47](http://tools.ietf.org/html/rfc5646) balises de langue ou paramètres régionaux telles que « en-US » et « Hans-zh-CN ». L’étiquette peut inclure la langue, la région, le pays et la variante. Pour obtenir la liste des langues, consultez la [IANA langue sous-balise du Registre](http://go.microsoft.com/fwlink/p/?linkid=227303). Pour obtenir des exemples de balises de langue, consultez [annexe A](http://tools.ietf.org/html/rfc5646#appendix-A) BCP 47. Pour `Collator`, vous pouvez inclure l’extension -u dans la chaîne de paramètres régionaux pour spécifier un ou plusieurs des extensions Unicode suivantes :  
  
-   -co pour spécifier les classements variants (spécifiques aux paramètres régionaux) : «*langage*-*région*-u-co -*valeur*».  
  
-   -kn pour spécifier une comparaison numérique : «*langage*-*région*- u-kn-true &#124; false ».  
  
-   -kf pour spécifier s’il faut trier tout d’abord les caractères majuscules ou minuscules : «*langage*-*région*- u-kf-supérieur &#124; inférieur &#124; false »). Cette extension n’est pas pris en charge actuellement.  
  
 Pour spécifier une comparaison numérique, vous pouvez définir l’extension -kn dans la chaîne de paramètres régionaux ou utiliser le `numeric` propriété dans le `options` paramètre. Si vous utilisez le `numeric` propriété, la valeur -kn ne s’appliquera pas.  
  
 Le paramètre `options` peut inclure les propriétés suivantes :  
  
-   `localeMatcher`. Spécifie l'algorithme de correspondance avec les paramètres régionaux à utiliser. Les valeurs possibles sont « rechercher » et « ajustement optimal ». La valeur par défaut est « ajuster ».  
  
-   `usage`. Spécifie si l’objectif de la comparaison est tri ou des recherches. Les valeurs possibles sont « sort » et « recherche ». La valeur par défaut est « trier ».  
  
-   `sensitivity`. Spécifie le critère de diffusion de l’assembleur. Les valeurs possibles sont « base », « accent », « incident » et « variant ». La valeur par défaut est `undefined`.  
  
-   `ignorePunctuation`. Spécifie si les signes de ponctuation sont ignorées dans la comparaison. Les valeurs possibles sont « true » et « false ». La valeur par défaut est `false`.  
  
-   `numeric`. Spécifie si le tri numérique est utilisé. Les valeurs possibles sont « true » et « false ». La valeur par défaut est `false`.  
  
-   `caseFirst`. Actuellement non pris en charge.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Collator`.  
  
|||  
|-|-|  
|Propriété|Description|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|Retourne une fonction qui compare deux chaînes à l’aide d’ordre de tri de l’assembleur.|  
|[constructeur](../../javascript/reference/constructor-property-intl-collator.md)|Spécifie la fonction qui crée un assembleur.|  
|[prototype](../../javascript/reference/prototype-property-intl-collator.md)|Retourne une référence au prototype pour un assembleur.|  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Collator`.  
  
|||  
|-|-|  
|Méthode|Description|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|Retourne un objet qui contient les propriétés et valeurs de l’assembleur.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un `Collator` de l’objet et effectue une comparaison.  
  
```JavaScript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise `Collator` objets à trier un tableau. Cet exemple montre les différences de paramètres régionaux.  
  
```JavaScript  
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
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un `Collator` pour rechercher une chaîne de l’objet et spécifie les options de comparaison.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [localeCompare, méthode (String)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Intl.DateTimeFormat, objet](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Objet Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)