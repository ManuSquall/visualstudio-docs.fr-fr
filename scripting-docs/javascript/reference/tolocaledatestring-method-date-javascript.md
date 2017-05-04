---
title: "toLocaleDateString, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "toLocaleDateString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleDateString (méthode)"
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# toLocaleDateString, m&#233;thode (Date) (JavaScript)
Retourne une date convertie en valeur de chaîne en fonction des paramètres régionaux définis pour l'environnement hôte ou de paramètres régionaux spécifiques.  
  
## Syntaxe  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### Paramètres  
 `dateObj`  
 Requis.  Objet `Date`.  
  
 `locales`  
 Optionnel.  Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux.  Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez\-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut.  Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés.  
  
 `options`  
 Optionnel.  Objet qui contient une ou plusieurs propriétés qui spécifient les options de comparaison.  
  
## Notes  
 À partir d'Internet Explorer 11, `toLocaleDateString` utilise `Intl.DateTimeFormat` en interne pour mettre en forme la date, ce qui ajoute la prise en charge des paramètres `locales` et `options`.  Pour plus d'informations sur ces paramètres, consultez [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Les paramètres `locales` et `options` ne sont pas pris en charge dans tous les modes de document et toutes les versions de navigateur.  Pour plus d'informations, consultez la section Configuration requise.  
  
 Lorsque vous utilisez `toLocaleDateString` en mode de document Internet Explorer 10 \(mode standard\), mode de document Internet Explorer versions antérieures, et mode Quirks :  
  
-   il retourne une valeur de chaîne contenant une date dans le fuseau actuel.  
  
-   La date retournée est exprimée dans le format par défaut défini par les paramètres régionaux de l'environnement hôte.  
  
 Si vous omettez le paramètre `locales`, la valeur de retour de cette méthode ne peut pas être utilisée de manière fiable dans un script, étant donné qu'elle varie d'un ordinateur à un autre.  Dans ce scénario, utilisez la méthode uniquement pour mettre en forme le texte – jamais dans le cadre d'un calcul.  
  
## Exemple  
 L'exemple suivant montre comment utiliser la méthode `toLocaleDateString` avec des paramètres régionaux spécifiés et des options de comparaison.  
  
```javascript  
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
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Paramètres `locales` et `options` :  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Voir aussi  
 [toDateString, méthode \(Date\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString, méthode \(Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)