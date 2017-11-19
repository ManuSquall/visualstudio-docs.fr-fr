---
title: "Méthodes de balisage HTML (JavaScript) | Documents Microsoft"
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
helpviewer_keywords:
- link method [JavaScript]
- blink method [JavaScript]
- fontsize method [JavaScript]
- italics method [JavaScript]
- sup method [JavaScript]
- anchor method [JavaScript]
- fixed method [JavaScript]
- fontcolor method [JavaScript]
- bold method [JavaScript]
- small method [JavaScript]
- HTML Tag methods [JavaScript]
- sub method [JavaScript]
- big method [JavaScript]
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7639bc609d8e9b7e4b212fe67ae40f81487d708e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="html-tag-methods-javascript"></a>méthodes de balisage HTML (JavaScript)
Vous pouvez utiliser des méthodes de balisage HTML pour placer des éléments HTML autour du texte dans un `String` objet.  
  
## <a name="syntax"></a>Syntaxe  
 Le tableau suivant répertorie la syntaxe et une description de chaque méthode de balise HTML.  
  
 Dans la colonne de la syntaxe, `string1` est un `String` littéral ou un objet.  
  
 La colonne Standard indique [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/?LinkId=199553) recommandations pour HTML 4. « Déconseillée » indique que l’élément HTML est déconseillé en faveur de feuilles de style.  
  
|Syntaxe|Description de la méthode|Description du paramètre|Standard|  
|------------|------------------------|---------------------------|--------------|  
|`string1`.Anchor (`name`)|Place un point d’ancrage HTML qui possède un attribut NAME autour du texte.|Le `name` paramètre est le texte à placer dans l’attribut de nom de l’ancre HTML.||  
|`string1`.Big()|Place la balise HTML \<BIG > autour du texte, les balises.||Déconseillé|  
|`string1`.blink()|Place la balise HTML \<BLINK > autour du texte, les balises. Le \<BLINK > balise n’est pas pris en charge dans Internet Explorer.||Dans la norme|  
|`string1`.Bold()|Place la balise HTML \<B > balises autour du texte.||Déconseillé|  
|`string1`.fixed()|Place la balise HTML \<TT > autour du texte, les balises.||Déconseillé|  
|`string1`.FontColor (`color`)|Place la balise HTML \<police > balises avec un attribut COLOR autour du texte.|Le `color` paramètre est une valeur de chaîne qui contient la valeur hexadécimale ou nom prédéfini pour une couleur. Les noms de couleur prédéfinis valides dépendent du [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] héberger le navigateur et sa version.|Déconseillé|  
|`string1`.FontSize (`size`)|Place la balise HTML \<police > balises avec un attribut SIZE autour du texte.|Le `size` paramètre est une valeur entière qui spécifie la taille du texte. Valeurs entières valides dépendent du [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] héberger le navigateur et sa version.|Déconseillé|  
|`string1`.italics()|Place la balise HTML \<I > balises autour du texte.||Déconseillé|  
|`string1`.Link (`href`)|Place un point d’ancrage HTML qui a un attribut HREF autour du texte.|Le `href` paramètre est le texte à placer dans l’attribut HREF d’ancrage HTML.||  
|`string1`.Small()|Place la balise HTML \<SMALL > autour du texte, les balises.||Déconseillé|  
|`string1`.Strike()|Place la balise HTML \<STRIKE > autour du texte, les balises.||Déconseillé|  
|`string1`.Sub()|Place la balise HTML \<SUB > balises autour du texte.|||  
|`string1`.sup()|Place la balise HTML \<SUP > balises autour du texte.|||  
  
## <a name="remarks"></a>Remarques  
 Aucune vérification n’est effectuée pour déterminer si les balises HTML ont déjà été appliquées à la chaîne.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent comment utiliser les méthodes de la balise HTML.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objet String](../../javascript/reference/string-object-javascript.md)