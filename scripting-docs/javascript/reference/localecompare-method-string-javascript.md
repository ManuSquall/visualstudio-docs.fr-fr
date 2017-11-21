---
title: "localeCompare, méthode (String) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: localeCompare
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: localeCompare method
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 056a440d26c4ebf48bd762968fa32ea1efdfb443
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="localecompare-method-string-javascript"></a>localeCompare, méthode (String) (JavaScript)
Détermine si deux chaînes sont équivalentes dans les paramètres régionaux actuels.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## <a name="parameters"></a>Paramètres  
 `stringVar`  
 Obligatoire. Première chaîne à comparer.  
  
 `stringExp`  
 Obligatoire. Deuxième chaîne à comparer.  
  
 `locales`  
 Facultatif. Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux. Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut. Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés. Ce paramètre doit être conforme à [BCP 47](http://tools.ietf.org/html/rfc5646) normes ; consultez la [Intl.Collator, objet](../../javascript/reference/intl-collator-object-javascript.md) pour plus d’informations.  
  
 `options`  
 Facultatif. Objet qui contient une ou plusieurs propriétés qui spécifient des options de comparaison. consultez le [Intl.Collator, objet](../../javascript/reference/intl-collator-object-javascript.md) pour plus d’informations.  
  
## <a name="remarks"></a>Remarques  
 Pour les chaînes de comparaison, vous pouvez spécifier soit `String` objets ou littéraux de chaîne.  
  
 À partir de Internet Explorer 11, `localeCompare` utilise le `Intl.Collator` de l’objet en interne pour effectuer des comparaisons, qui ajoute la prise en charge pour le `locales` et `options` paramètres. Pour plus d’informations sur ces paramètres, consultez [Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) et [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md).  
  
> [!IMPORTANT]
>  Les paramètres `locales` et `options` ne sont pas pris en charge dans tous les modes de document et les versions de navigateur. Pour plus d’informations, consultez la section Exigences.  
  
 Le `localeCompare` méthode effectue une comparaison de chaînes sensible aux paramètres régionaux de `stringVar` et `stringExp` et retourne une de ces résultats, selon l’ordre de tri des paramètres régionaux système par défaut :  
  
-   -1 si `stringVar` trie avant `stringExp`.  
  
-   + 1 si `stringVar` après `stringExp`.  
  
-   0 (zéro) si les deux chaînes sont équivalentes.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser `localeCompare`.  
  
```JavaScript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser `localeCompare` avec les paramètres régionaux allemand (Allemagne).  
  
```JavaScript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser `localeCompare` avec les paramètres régionaux allemand (Allemagne) et une extension spécifique aux paramètres régionaux qui spécifie l’ordre de tri pour les annuaires en allemand. Cet exemple montre les différences de paramètres régionaux.  
  
```JavaScript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Paramètres `locales` et `options` :  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode toLocaleString (Object)](../../javascript/reference/tolocalestring-method-object-javascript.md)