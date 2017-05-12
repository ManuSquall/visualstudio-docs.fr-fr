---
title: "toLocaleString (Number) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# toLocaleString (Number)
Convertit un nombre en une chaîne en utilisant les paramètres régionaux actuels ou spécifiés.  
  
## Syntaxe  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### Paramètres  
 `numberObj`  
 Requis.  Objet `Number` à convertir.  
  
 `locales`  
 Optionnel.  Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux.  Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez\-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut.  Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés.  
  
 `options`  
 Optionnel.  Objet qui contient une ou plusieurs propriétés qui spécifient les options de comparaison.  
  
## Notes  
 À partir d'Internet Explorer 11, `toLocaleString` utilise `Intl.NumberFormat` en interne pour effectuer des comparaisons, ce qui ajoute la prise en charge des paramètres `locales` et `options`.  Pour plus d'informations sur ces paramètres, consultez [Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Les paramètres `locales` et `options` ne sont pas pris en charge dans tous les modes de document et toutes les versions de navigateur.  Pour plus d'informations, consultez la section Configuration requise.  
  
> [!NOTE]
>  Si vous omettez le paramètre `locales`, utilisez `toLocaleString` pour afficher uniquement les résultats à un utilisateur ; ne l'utilisez jamais pour calculer des valeurs dans un script, car le résultat retourné est propre à l'ordinateur \(la méthode retourne les paramètres régionaux\).  
  
## Exemple  
 L'exemple suivant décrit comment utiliser la méthode `toLocaleString` sans paramètre.  
  
```javascript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## Exemple  
 L'exemple suivant montre comment utiliser la méthode `toLocaleString` avec des paramètres régionaux spécifiés et des options de comparaison.  
  
```javascript  
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
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Paramètres `locales` et `options` :  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Voir aussi  
 [toLocaleDateString, méthode \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)