---
title: "toLocaleString (Date) | Microsoft Docs"
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
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# toLocaleString (Date)
Convertit une date en chaîne en utilisant les paramètres régionaux actuels ou spécifiés.  
  
## Syntaxe  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### Paramètres  
 `dateObj`  
 Requis.  Objet `Date` à convertir.  
  
 `locales`  
 Optionnel.  Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux.  Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez\-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut.  Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés.  
  
 `options`  
 Optionnel.  Objet qui contient une ou plusieurs propriétés qui spécifient les options de comparaison.  
  
## Notes  
 À partir d'Internet Explorer 11, `toLocaleString` utilise `Intl.DateTimeFormat` en interne pour effectuer des comparaisons, ce qui ajoute la prise en charge des paramètres `locales` et `options`.  Pour plus d'informations sur ces paramètres, consultez [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Les paramètres `locales` et `options` ne sont pas pris en charge dans tous les modes de document et toutes les versions de navigateur.  Pour plus d'informations, consultez la section Configuration requise.  
  
 Lorsque vous utilisez `toLocaleString` en mode de document Internet Explorer 10 \(mode standard\), mode de document Internet Explorer versions antérieures, et mode Quirks :  
  
-   Elle retourne un objet `String` qui contient la date écrite dans le format long par défaut spécifié dans les paramètres régionaux en cours.  
  
-   Pour les dates comprises entre 1601 et 1999 après J.\-C., la date est écrite dans le format correspondant aux paramètres régionaux du Panneau de configuration.  
  
> [!NOTE]
>  Si vous omettez le paramètre `locales`, utilisez `toLocaleString` pour afficher uniquement les résultats à un utilisateur ; ne l'utilisez jamais pour calculer des valeurs dans un script, car le résultat retourné est propre à l'ordinateur.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `toLocaleString`.  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## Exemple  
 L'exemple suivant montre comment utiliser la méthode `toLocaleString` avec des paramètres régionaux spécifiés et des options de comparaison.  
  
```javascript  
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
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Paramètres `locales` et `options` :  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Voir aussi  
 [toLocaleDateString, méthode \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)