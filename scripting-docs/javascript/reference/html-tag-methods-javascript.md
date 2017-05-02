---
title: "m&#233;thodes de balisage&#160;HTML (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "anchor (méthode) (JavaScript)"
  - "big (méthode) (JavaScript)"
  - "blink (méthode) (JavaScript)"
  - "bold (méthode) (JavaScript)"
  - "fixed (méthode) (JavaScript)"
  - "fontcolor (méthode) (JavaScript)"
  - "fontsize (méthode) (JavaScript)"
  - "méthodes relatives aux balises HTML (JavaScript)"
  - "italics (méthode) (JavaScript)"
  - "link (méthode) (JavaScript)"
  - "small (méthode) (JavaScript)"
  - "sub (méthode) (JavaScript)"
  - "sup (méthode) (JavaScript)"
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# m&#233;thodes de balisage&#160;HTML (JavaScript)
Vous pouvez utiliser les méthodes de balisage HTML pour placer des éléments HTML autour du texte d'un objet `String`.  
  
## Syntaxe  
 Le tableau suivant répertorie la syntaxe et la description de chaque méthode de balisage HTML.  
  
 Dans la colonne Syntaxe, `string1` est un objet ou un littéral `String`.  
  
 La colonne Standard présente les recommandations du [World Wide Web Consortium \(W3C\)](http://go.microsoft.com/fwlink/?LinkId=199553) pour HTML 4.  « Déconseillé » indique que l'élément HTML est déconseillé et que l'utilisation de feuilles de style est préférable.  
  
|Syntaxe|Description de la méthode|Description des paramètres|Standard|  
|-------------|-------------------------------|--------------------------------|--------------|  
|`string1`.anchor\(`name`\)|Place un point d'ancrage HTML comprenant un attribut NAME autour du texte.|Le paramètre `name` correspond au texte à ajouter à l'attribut NAME du point d'ancrage HTML.||  
|`string1`.big\(\)|Place des balises HTML \<BIG\> autour du texte.||Déconseillé|  
|`string1`.blink\(\)|Place des balises HTML \<BLINK\> autour du texte.  La balise \<BLINK\> n'est pas prise en charge dans Internet Explorer.||Pas en mode standard|  
|`string1`.bold\(\)|Place des balises HTML \<B\> autour du texte.||Déconseillé|  
|`string1`.fixed\(\)|Place des balises HTML \<TT\> autour du texte.||Déconseillé|  
|`string1`.fontcolor\(`color`\)|Place des balises HTML \<FONT\> avec un attribut COLOR autour du texte.|Le paramètre `color` est une valeur de chaîne qui contient la valeur hexadécimale ou le nom prédéfini d'une couleur.  Les noms de couleurs prédéfinis valides dépendent du navigateur hôte [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] et de sa version.|Déconseillé|  
|`string1`.fontsize\(`size`\)|Place des balises HTML \<FONT\> avec un attribut SIZE autour du texte.|Le paramètre `size` est une valeur entière qui spécifie la taille du texte.  Les valeurs entières valides dépendent du navigateur hôte [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] et de sa version.|Déconseillé|  
|`string1`.italics\(\)|Place des balises HTML \<I\> autour du texte.||Déconseillé|  
|`string1`.link\(`href`\)|Place un point d'ancrage HTML comprenant un attribut HREF autour du texte.|Le paramètre `href` correspond au texte à ajouter à l'attribut HREF du point d'ancrage HTML.||  
|`string1`.small\(\)|Place des balises HTML \<SMALL\> autour du texte.||Déconseillé|  
|`string1`.strike\(\)|Place des balises HTML \<STRIKE\> autour du texte.||Déconseillé|  
|`string1`.sub\(\)|Place des balises HTML \<SUB\> autour du texte.|||  
|`string1`.sup\(\)|Place des balises HTML \<SUP\> autour du texte.|||  
  
## Remarques  
 Aucun contrôle n'est effectué pour déterminer si les balises HTML ont déjà été appliquées à la chaîne.  
  
## Exemple  
 Les exemples suivants illustrent l'utilisation des méthodes de balisage HTML.  
  
```javascript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [String, objet](../../javascript/reference/string-object-javascript.md)