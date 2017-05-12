---
title: "localeCompare, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "localeCompare"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "localeCompare (méthode)"
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# localeCompare, m&#233;thode (String) (JavaScript)
Détermine si deux chaînes sont équivalentes dans les paramètres régionaux.  
  
## Syntaxe  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## Paramètres  
 `stringVar`  
 Requis.  Première chaîne à comparer.  
  
 `stringExp`  
 Requis.  Deuxième chaîne à comparer.  
  
 `locales`  
 Optionnel.  Tableau de chaînes de paramètres régionaux qui contiennent une ou plusieurs balises de langue ou de paramètres régionaux.  Si vous incluez plusieurs chaînes de paramètres régionaux, répertoriez\-les dans l'ordre de priorité décroissant afin que la première entrée soit la valeur par défaut.  Si vous omettez ce paramètre, les paramètres régionaux par défaut du runtime JavaScript sont utilisés.  Ce paramètre doit être conforme aux normes [BCP 47](http://tools.ietf.org/html/rfc5646). Consultez la section relative à l'[objet Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) pour plus de détails.  
  
 `options`  
 Optionnel.  Un objet qui contient une ou plusieurs propriétés qui spécifient des options de comparaison. consultez [Intl.Collator object](../../javascript/reference/intl-collator-object-javascript.md) pour plus de détails.  
  
## Notes  
 Pour les chaînes de comparaison, vous pouvez spécifier des objets `String` ou des littéraux de chaîne.  
  
 À partir d'Internet Explorer 11, `localeCompare` utilise l'objet `Intl.Collator` en interne pour effectuer des comparaisons, ce qui ajoute la prise en charge des paramètres `locales` et `options`.  Pour plus d'informations sur ces paramètres, consultez [Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) et [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md).  
  
> [!IMPORTANT]
>  Les paramètres `locales` et `options` ne sont pas pris en charge dans tous les modes de document et toutes les versions de navigateur.  Pour plus d'informations, consultez la section Configuration requise.  
  
 La méthode `localeCompare` effectue une comparaison de chaînes sensible aux paramètres locaux de `stringVar` et `stringExp` et retourne l'un des résultats suivants, en fonction de l'ordre de tri des paramètres régionaux par défaut du système :  
  
-   \-1 si `stringVar` est placé avant dans l'ordre de tri `stringExp`.  
  
-   \+1 si `stringVar` est trié après `stringExp`.  
  
-   0 \(zéro\) si les deux chaînes sont équivalentes.  
  
## Exemple  
 Le code suivant montre comment utiliser `localeCompare` :  
  
```javascript  
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
  
## Exemple  
 Le code suivant montre comment utiliser `localeCompare` avec les paramètres régionaux allemands \(Allemagne\).  
  
```javascript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## Exemple  
 L'exemple suivant montre comment utiliser `localeCompare` avec les paramètres régionaux allemands \(Allemagne\) et une extension spécifique aux paramètres régionaux qui spécifie l'ordre de tri pour les annuaires téléphoniques allemands.  Cet exemple illustre les différences spécifiques aux paramètres régionaux.  
  
```javascript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Paramètres `locales` et `options` :  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Voir aussi  
 [toLocaleString, méthode \(Object\)](../../javascript/reference/tolocalestring-method-object-javascript.md)