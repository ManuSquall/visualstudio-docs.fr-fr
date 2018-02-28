---
title: "Split, méthode (String) (JavaScript) | Documents Microsoft"
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
- split
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- split method
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eea90dda2e8e4d52451af247d139eeee44f83917
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="split-method-string-javascript"></a>split, méthode (String) (JavaScript)
Fractionner une chaîne en sous-chaînes à l'aide du séparateur spécifié et les retourner sous la forme d'un tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## <a name="parameters"></a>Paramètres  
 `stringObj`  
 Obligatoire. Objet `String` ou littéral de chaîne à fractionner. Cet objet n’est pas modifié par le **fractionner** (méthode).  
  
 `separator`  
 Facultatif. Une chaîne ou d’une **Expression régulière** objet qui identifie l’ou les caractères à utiliser pour fractionner la chaîne. Si cet argument est omis, la méthode retourne un tableau à un seul élément contenant la chaîne entière.  
  
 `limit`  
 Facultatif. Valeur utilisée pour limiter le nombre d'éléments retournés dans le tableau.  
  
## <a name="return-value"></a>Valeur de retour  
 Le résultat de la **fractionner** méthode est un tableau de chaînes fractionné à chaque endroit où `separator` se produit dans `stringObj`. L'argument `separator` n'est pas retourné comme partie d'un élément du tableau.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **fractionner** (méthode).  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [concat, méthode (String)](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp (objet)](../../javascript/reference/regexp-object-javascript.md)   
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Exemple d’application de défilement, panoramique et zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)