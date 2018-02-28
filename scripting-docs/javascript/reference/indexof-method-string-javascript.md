---
title: "Méthode indexOf (chaîne) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- indexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- indexOf method, string
- string, indexOf method
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecd96acb21f9d7711f9ee00dbf1c1bb70705c0d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="indexof-method-string-javascript"></a>indexOf, méthode (String) (JavaScript)
Retourne la position de la première occurrence d'une sous-chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## <a name="parameters"></a>Paramètres  
 `strObj`  
 Obligatoire. A `String` objet ou un littéral de chaîne.  
  
 `subString`  
 Obligatoire. Sous-chaîne à rechercher dans la chaîne  
  
 `startIndex`  
 Facultatif. Index à partir duquel commencer la recherche de l'objet `String`. Si ce paramètre est omis, la recherche commence au début de la chaîne.  
  
## <a name="remarks"></a>Remarques  
 Le **indexOf** méthode retourne le début de la sous-chaîne dans la `String` objet. Si la sous-chaîne est introuvable, la valeur -1 est retournée.  
  
 Si `startindex` est négatif, `startindex` est considéré comme égal à 0 (zéro). S'il est supérieur à l'index le plus élevé, il est considéré comme l'index le plus grand possible.  
  
 La recherche est effectuée de gauche à droite. Sinon, cette méthode est identique à **lastIndexOf**.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **indexOf** (méthode).  
  
```JavaScript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode lastIndexOf (chaîne)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [Exemple d’application de défilement, panoramique et zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)