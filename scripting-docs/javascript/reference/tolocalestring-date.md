---
title: toLocaleString (Date) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6dc7b1f38f7e57d1c10f7197bb73b13b3545380
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-date"></a>toLocaleString (Date)
Convertit une date en une chaîne à l’aide de paramètres régionaux actuelle ou spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Paramètres  
 `dateObj`  
 Obligatoire. Objet `Date` à convertir.  
  
 `locales`  
 Facultatif. Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux. Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut. Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés.  
  
 `options`  
 Facultatif. Objet qui contient une ou plusieurs propriétés qui spécifient des options de comparaison.  
  
## <a name="remarks"></a>Remarques  
 À partir de Internet Explorer 11, `toLocaleString` utilise `Intl.DateTimeFormat` en interne pour les comparaisons de marque, qui ajoute la prise en charge pour le `locales` et `options` paramètres. Pour plus d’informations sur ces paramètres, consultez [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Les paramètres `locales` et `options` ne sont pas pris en charge dans tous les modes de document et les versions de navigateur. Pour plus d'informations, consultez la section Configuration requise.  
  
 Lorsque vous utilisez `toLocaleString` en mode de document standard Internet Explorer 10, dans les modes de document précédents et en mode Quirks :  
  
-   Elle retourne un `String` objet qui contient la date écrite sous forme de long par défaut de paramètres régionaux actuels.  
  
-   Pour les dates entre 1601 et 1999 J.-C., la date est mise en forme en fonction des paramètres régionaux du Panneau de configuration de l’utilisateur.  
  
> [!NOTE]
>  Si vous omettez le `locales` paramètre, utilisez `toLocaleString` que pour afficher les résultats à l’utilisateur ; jamais les utiliser pour calculer les valeurs dans un script, car le résultat retourné est spécifiques à l’ordinateur.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `toLocaleString`.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser la méthode `toLocaleString` avec des options de comparaison et de paramètres régionaux spécifiées.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Paramètres `locales` et `options` :  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)