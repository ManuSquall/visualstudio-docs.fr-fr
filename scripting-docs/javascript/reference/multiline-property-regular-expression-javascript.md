---
title: MultiLine, propriété (Regular Expression) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- multiline
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- multiline property
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 289cb8d8e103d8c4ac1b1ef06714105d21cba743
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639649"
---
# <a name="multiline-property-regular-expression-javascript"></a>multiline, propriété (Regular Expression) (JavaScript)
Retourne une valeur booléenne qui indique l’état de l’indicateur multiline (**m**) utilisé dans une expression régulière. Valeur par défaut est **false**. Lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
rgExp.multiline  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `rgExp` argument est une instance de la `RegExp` objet  
  
 Le **multiligne** propriété renvoie **true** si l’indicateur multiline est défini pour une expression régulière et retourne **false** si elle n’est pas. Le **multiligne** propriété **true** si l’objet d’expression régulière a été créé avec le **m** indicateur.  
  
 Si **multiligne** est **false**, « ^ » correspond à la position au début d’une chaîne et correspond à la « $» à la fin d’une chaîne. Si **multiligne** est **true**, « ^ » correspond à la position au début de chaîne ainsi qu’à la position qui suit un « \n » ou « \r » et « $» correspond à la position à la fin d’une chaîne » \n « ou « \r ».  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre le comportement de la **multiligne** propriété. Si vous passez « m » à la fonction indiquée ci-dessous, le mot « while » est remplacé par le mot « et ». Effet avec l’indicateur multiline est défini, et le mot « while » se produit au début de la ligne après un caractère de saut de ligne. L’indicateur multiligne permet la recherche à effectuer sur des chaînes multilignes.  
  
```JavaScript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S’applique aux**: [objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [global, propriété (Regular Expression)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [IgnoreCase, propriété (Regular Expression)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)