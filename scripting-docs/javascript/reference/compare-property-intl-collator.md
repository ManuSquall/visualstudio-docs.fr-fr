---
title: comparer la propriété (Intl.Collator) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bfd222ac8d2c94efe279177e7f4d8ffdf850f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634169"
---
# <a name="compare-property-intlcollator"></a>compare, propriété (Intl.Collator)
Retourne une fonction qui compare deux chaînes à l’aide d’ordre de tri de l’assembleur.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
collatorObj.compare  
```  
  
#### <a name="parameters"></a>Paramètres  
 `collatorObj`  
 Obligatoire. Le nom de la `Collator` objet à utiliser pour la comparaison.  
  
## <a name="remarks"></a>Remarques  
 La fonction retournée par le `compare` propriété accepte deux arguments, `x` et `y`et retourne le résultat d’une comparaison de paramètres régionaux spécifiques de `x` et `y` en utilisant les options spécifiées dans le `Collator` objet.  
  
 Le résultat de la comparaison sera :  
  
-   -1 si `x` avant `y` dans l’ordre de tri.  
  
-   0 (zéro) si `x` est égal à `y` dans l’ordre de tri.  
  
-   1 si `x` après `y` dans l’ordre de tri.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un `Collator` de l’objet et effectue une comparaison.  
  
```JavaScript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
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
 L’exemple suivant utilise un `Collator` objet pour rechercher une chaîne.  
  
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
 [Objet Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)