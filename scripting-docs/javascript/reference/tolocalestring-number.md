---
title: toLocaleString (nombre) | Documents Microsoft
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
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b5e6378ec94e032c908a3502c0324c2a5a91b26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640829"
---
# <a name="tolocalestring-number"></a>toLocaleString (Number)
Convertit un nombre en une chaîne à l’aide de paramètres régionaux actuelle ou spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Paramètres  
 `numberObj`  
 Obligatoire. Objet `Number` à convertir.  
  
 `locales`  
 Facultatif. Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux. Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut. Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés.  
  
 `options`  
 Facultatif. Objet qui contient une ou plusieurs propriétés qui spécifient des options de comparaison.  
  
## <a name="remarks"></a>Remarques  
 À partir de Internet Explorer 11, `toLocaleString` utilise `Intl.NumberFormat` en interne pour les comparaisons de marque, qui ajoute la prise en charge pour le `locales` et `options` paramètres. Pour plus d’informations sur ces paramètres, consultez [Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Les paramètres `locales` et `options` ne sont pas pris en charge dans tous les modes de document et les versions de navigateur. Pour plus d’informations, consultez la section Exigences.  
  
> [!NOTE]
>  Si vous omettez le `locales` paramètre, utilisez `toLocaleString` que pour afficher les résultats à l’utilisateur ; jamais les utiliser pour calculer les valeurs dans un script, car le résultat retourné est spécifique à l’ordinateur (la méthode retourne les paramètres régionaux).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la `toLocaleString` méthode sans paramètres.  
  
```JavaScript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser la méthode `toLocaleString` avec des options de comparaison et de paramètres régionaux spécifiées.  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Paramètres `locales` et `options` :  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)