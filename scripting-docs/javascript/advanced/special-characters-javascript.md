---
title: Caractères spéciaux (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- line terminator character
- white space character
- Unicode character
- escape sequence
- backslash (\)
ms.assetid: 3b38b1bd-1f0f-4748-b13e-55cab36fd126
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0eaae8dfc84d9a3be6db54c50558d4cf675a53a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569629"
---
# <a name="special-characters-javascript"></a>Caractères spéciaux (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fournit des séquences d'échappement que vous pouvez inclure dans des chaînes pour créer des caractères que vous ne pouvez pas taper directement.  
  
## <a name="remarks"></a>Notes  
 Une valeur de chaîne est une série de zéro ou plusieurs caractères Unicode (lettres, chiffres et autres caractères). Les littéraux de chaîne sont placés entre des paires de guillemets simples ou doubles correspondantes. Des guillemets doubles peuvent être contenus dans une chaîne placée entre guillemets simples. Des guillemets simples peuvent être contenus dans une chaîne placée entre guillemets doubles.  
  
 Chaque caractère dans un littéral de chaîne peut être représenté par une séquence d'échappement. Une séquence d’échappement commence par une barre oblique inverse (\\) qui informe l’interpréteur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que le caractère suivant est un caractère spécial.  
  
 Vous pouvez spécifier un caractère Unicode en utilisant la séquence d’échappement \u*hhhh*, où *hhhh* est un nombre hexadécimal à quatre chiffres. Une séquence d'échappement Unicode peut représenter n'importe quel caractère de 16 bits. Pour plus d’informations, consultez [Séquences d’échappement de point de code Unicode](#CodePoint).  
  
 Vous pouvez utiliser une séquence d'échappement à un seul caractère pour certains caractères. Par exemple, \t spécifie un caractère de tabulation.  
  
## <a name="escape-sequences"></a>Séquences d'échappement  
 Le tableau suivant répertorie quelques exemples de séquences d'échappement pour des caractères courants.  
  
|Valeur de caractère Unicode|Séquence d'échappement|Signification|Catégorie|  
|-----------------------------|---------------------|-------------|--------------|  
|\u0008|\b|Retour arrière||  
|\u0009|\t|Onglet|Espace blanc|  
|\u000A|\n|Saut de ligne (nouvelle ligne)|Marque de fin de ligne|  
|\u000B|\v<br /><br /> (Voir la remarque après ce tableau.)|Tabulation verticale|Espace blanc|  
|\u000C|\f|Saut de page|Espace blanc|  
|\u000D|\r|Retour chariot|Marque de fin de ligne|  
|\u0020||Espace|Espace blanc|  
|\u0022|\\"|Guillemet double (")||  
|\u0027|\\'|Guillemet simple (')||  
|\u005C|\\\|Barre oblique inverse (\\)||  
|\u00A0||Espace insécable|Espace blanc|  
|\u2028||Séparateur de ligne|Marque de fin de ligne|  
|\u2029||Séparateur de paragraphe|Marque de fin de ligne|  
|\uFEFF||Marque d'ordre d'octet|Espace blanc|  
  
 La colonne Catégorie spécifie si le caractère est un espace blanc ou une marque de fin de ligne. La [méthode trim (String)](../../javascript/reference/trim-method-string-javascript.md) supprime les espaces de début et de fin ainsi que la marque de fin de ligne d’une chaîne.  
  
 La barre oblique inverse elle-même est utilisée comme caractère d'échappement. Par conséquent, vous ne pouvez pas en taper une directement dans votre script. Si vous souhaitez écrire une barre oblique inverse, vous devez en taper deux (\\\\).  
  
> [!NOTE]
>  Depuis [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)], vous ne pouvez pas identifier le navigateur comme Internet Explorer en testant l'équivalence de l'onglet vertical (\v) et du « v ». Dans les versions antérieures, l'expression `"\v" === "v"` retourne `true`. Dans [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)], l'expression retourne `false`.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant illustre les séquences d’échappement \\\ et \\.  
  
### <a name="code"></a>Code  
  
```JavaScript  
document.write('The image path is C:\\webstuff\\mypage\\gifs\\garden.gif.');  
document.write ("<br />");  
document.write('The caption reads, "After the snow of \'97. Grandma\'s house is covered."');  
```  
  
<a name="CodePoint"></a>   
## <a name="unicode-code-point-escape-sequences"></a>Séquences d'échappement de point de code Unicode  
 En [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)], Unicode est entièrement pris en charge. Les points de code Unicode les plus courants sont représentés par quatre chiffres hexadécimaux, par exemple /u0009 pour un caractère de tabulation. Les points de code astral, qui incluent tous les symboles qui nécessitent plus de quatre chiffres hexadécimaux, sont maintenant pris en charge sous un format simplifié. En utilisant le format "\u{*codepoint*}", l’ensemble des caractères Unicode peut être représenté au format littéral. Par exemple, pour représenter le symbole « 𠮷 », vous pouvez utiliser le format suivant : "\u{20BB7}".  
  
 Dans l'exemple de code suivant, les chaînes sont toutes équivalentes. (\uD842\uDFB7 est la méthode de la solution de contournement pour spécifier ce symbole dans les versions précédentes).  
  
```JavaScript  
"\u{20BB7}"=="𠮷"=="\uD842\uDFB7"  
```  
  
 RegExp inclut désormais un indicateur /u pour activer la prise en charge complète des points de code astral. Par exemple, dans l'exemple de code suivant, l'indicateur /u dans l'expression régulière permet la mise en correspondance des points de code astral (le point correspond à n'importe quel caractère dans la chaîne fournie).  
  
```JavaScript  
"𠮷".match(/./u)[0].length == 2  
```  
  
 L'indicateur /u permet l'analyse du nouveau format, \u{pointdecode}), comme séquence d'échappement Unicode. Cela est nécessaire, car \u{xxxxx} sans l'indicateur /u a une signification différente dans une expression régulière.  
  
> [!NOTE]
>  Pour les points de code astral, la longueur est toujours égale à 2. Cela correspond au comportement dans les versions précédentes.  
  
 L'objet String inclut maintenant deux nouvelles méthodes, String.codePointAt et String.fromCodePoint, pour prendre en charge les points de code astral. Par exemple, vous pouvez utiliser codePointAt pour retourner le point de code équivalent pour le symbole « 𠮷 ».  
  
```JavaScript  
"𠮷".codePointAt(0) == 0x20BB7  
  
```  
  
 Vous pouvez également parcourir les points de code à l'aide de l'instruction `for...of`.  
  
```JavaScript  
for(var c of "𠮷") {  
    console.log(c);  
}  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)