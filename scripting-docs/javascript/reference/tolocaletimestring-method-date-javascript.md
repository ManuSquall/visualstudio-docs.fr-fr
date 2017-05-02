---
title: "toLocaleTimeString, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "toLocaleTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleTimeString (méthode)"
ms.assetid: 8ad75bf5-864c-4a2a-be90-220e87dce172
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# toLocaleTimeString, m&#233;thode (Date) (JavaScript)
Retourne une heure en tant que valeur de chaîne adaptée aux paramètres régionaux actuels de l'environnement hôte ou à des paramètres régionaux spécifiés.  
  
## Syntaxe  
  
```  
  
dateObj.toLocaleTimeString([locales][, options])  
```  
  
#### Paramètres  
 `dateObj`  
 Obligatoire.  Objet `Date`.  
  
 `locales`  
 Facultatif.  Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux.  Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez\-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut.  Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés.  
  
 `options`  
 Facultatif.  Objet qui contient une ou plusieurs propriétés qui spécifient des options de comparaison.  
  
## Notes  
 À partir d'Internet Explorer 11, `toLocaleTimeString` utilise `Intl.DateTimeFormat` en interne pour mettre en forme l'heure, ce qui ajoute la prise en charge des paramètres `locales` et `options`.  Pour plus d'informations sur ces paramètres, consultez [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Les paramètres `locales` et `options` ne sont pas pris en charge dans tous les modes de document et les versions de navigateur.  Pour plus d'informations, consultez la section Configuration requise.  
  
 Lorsque vous utilisez `toLocaleTimeString` en mode de document standard Internet Explorer 10, dans les modes de document précédents et en mode Quirks :  
  
-   Elle retourne une valeur de chaîne qui contient une heure dans le fuseau horaire actuel.  
  
-   L'heure retournée est au format par défaut des paramètres régionaux actuels de l'environnement hôte.  
  
 Si vous omettez le paramètre `locales`, vous ne pouvez pas vous fier à la valeur de retour de cette méthode dans un script, car elle varie d'un ordinateur à l'autre.  Dans ce scénario, utilisez la méthode uniquement pour mettre en forme le texte affiché, et jamais dans le cadre d'un calcul.  
  
## Exemple  
 L'exemple suivant montre comment utiliser la méthode `toLocaleTimeString` avec des options de comparaison et de paramètres régionaux spécifiées.  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleTimeString("en-US"));  
document.write(date.toLocaleTimeString("ja-JP"));  
document.write(date.toLocaleTimeString("ar-SA", options));  
document.write(date.toLocaleTimeString("hi-IN", options));  
  
// Output:  
// ‎‎6‎:‎00‎:‎00‎ ‎AM ‎   
// 6‎:‎00‎:‎00‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤ ٠٦‎:‎٠٠‎:‎٠٠‎ ‎ص  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013 06:00:00  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Paramètres `locales` et `options` :  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Voir aussi  
 [toTimeString, méthode \(Date\)](../../javascript/reference/totimestring-method-date-javascript.md)   
 [toLocaleDateString, méthode \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)