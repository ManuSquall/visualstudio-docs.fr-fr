---
title: toLocaleDateString, méthode (Date) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- toLocaleDateString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleDateString method
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b4b019ad329a73bec13766932fbcadfa2ed133
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641279"
---
# <a name="tolocaledatestring-method-date-javascript"></a>toLocaleDateString, méthode (Date) (JavaScript)
Retourne une date sous la forme d’une valeur de chaîne qui est appropriée pour les paramètres régionaux de l’environnement hôte ou les paramètres régionaux spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Objet `Date`.  
  
 `locales`  
 Facultatif. Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux. Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut. Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés.  
  
 `options`  
 Facultatif. Objet qui contient une ou plusieurs propriétés qui spécifient des options de comparaison.  
  
## <a name="remarks"></a>Remarques  
 À partir de Internet Explorer 11, `toLocaleDateString` utilise `Intl.DateTimeFormat` en interne à mettre en forme la date, qui ajoute la prise en charge pour le `locales` et `options` paramètres. Pour plus d’informations sur ces paramètres, consultez [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Les paramètres `locales` et `options` ne sont pas pris en charge dans tous les modes de document et les versions de navigateur. Pour plus d'informations, consultez la section Configuration requise.  
  
 Lorsque vous utilisez `toLocaleDateString` en mode de document standard Internet Explorer 10, dans les modes de document précédents et en mode Quirks :  
  
-   Retourne une valeur de chaîne qui contient une date dans le fuseau horaire actuel.  
  
-   La date renvoyée est dans le format par défaut des paramètres régionaux actuels de l’environnement hôte.  
  
 Si vous omettez le paramètre `locales`, vous ne pouvez pas vous fier à la valeur de retour de cette méthode dans un script, car elle varie d'un ordinateur à l'autre. Dans ce scénario, utilisez la méthode uniquement au texte de format d’affichage - jamais dans le cadre d’un calcul.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser la méthode `toLocaleDateString` avec des options de comparaison et de paramètres régionaux spécifiées.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Paramètres `locales` et `options` :  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [toDateString, méthode (Date)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [Méthode toLocaleTimeString (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)