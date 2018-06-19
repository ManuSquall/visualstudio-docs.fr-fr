---
title: leftContext, propriété ($') (RegExp) (JavaScript) | Documents Microsoft
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
- $`
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- leftContext property ($`)
ms.assetid: 840e56c0-eb7c-461f-bb56-91acff9b5bcf
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0234a547d2e26c6cf6b1d1a058a46135e577fdd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637799"
---
# <a name="leftcontext-property--regexp-javascript"></a>leftContext, propriété ($') (RegExp) (JavaScript)
Retourne les caractères à partir du début d’une chaîne recherchée jusqu'à la position avant le début de la dernière correspondance. Lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RegExp.leftContext  
```  
  
## <a name="remarks"></a>Remarques  
 L’objet associé à cette propriété est toujours global `RegExp` objet.  
  
 La valeur initiale de la `leftContext` propriété est une chaîne vide. La valeur de la `leftContext` propriété change chaque fois qu’une correspondance réussie est établie.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de la propriété `leftContext` :  
  
```JavaScript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S’applique aux**: [RegExp (objet)](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [$1... $9, propriétés (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [index, propriété (RegExp)](../../javascript/reference/index-property-regexp-javascript.md)   
 [Propriété Input ($_) (RegExp)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [lastIndex, propriété (RegExp)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [lastMatch, propriété ($&) (RegExp)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [Propriété lastParen ($ +) (RegExp)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [Propriété rightContext ($') (RegExp)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)