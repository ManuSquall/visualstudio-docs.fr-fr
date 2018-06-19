---
title: rightContext, propriété ($&#39;) (RegExp) (JavaScript) | Documents Microsoft
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
- $'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- rightContext property ($')
ms.assetid: 6999c056-d18c-4583-9dd9-8fbb6d3d0ee7
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d47ea5dd67de9d73ab59b615c567ad3a7a96fb7b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640099"
---
# <a name="rightcontext-property-39-regexp-javascript"></a>rightContext, propriété ($&#39;) (RegExp) (JavaScript)
Retourne les caractères à partir de la position qui suit la dernière correspondance à la fin de la chaîne recherchée. Lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RegExp.rightContext  
```  
  
## <a name="remarks"></a>Remarques  
 L’objet associé à cette propriété est toujours global `RegExp` objet.  
  
 La valeur initiale de la **rightContext** propriété est une chaîne vide. La valeur de la **rightContext** propriété change chaque fois qu’une correspondance réussie est établie.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **rightContext** propriété :  
  
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
 [Propriété leftContext ($`) (RegExp)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)