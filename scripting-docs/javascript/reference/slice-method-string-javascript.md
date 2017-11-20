---
title: "slice, méthode (String) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], returning characters
- slice method
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1baa0a05a2d6aa8c06cc962761c8e557632d034c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-string-javascript"></a>slice, méthode (String) (JavaScript)
Retourne une section de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Paramètres  
 `stringObj`  
 Obligatoire. Objet `String` ou littéral de chaîne.  
  
 `start`  
 Obligatoire. L’index de début de la partie spécifiée des `stringObj`.  
  
 `end`  
 Facultatif. L’index à la fin de la partie spécifiée des `stringObj`. La sous-chaîne inclut tous les caractères jusqu'à, mais non compris le caractère indiqué par `end`. Si cette valeur n’est pas spécifiée, la sous-chaîne continue jusqu'à la fin de `stringObj`.  
  
## <a name="remarks"></a>Remarques  
 Le `slice` méthode retourne un `String` objet contenant la partie spécifiée des `stringObj`.  
  
 Le `slice` méthode copie les, mais sans inclure le caractère indiqué par `end`.  
  
 Si `start` est négatif, il est traité comme *longueur*  +  `start` où *longueur* est la longueur de la chaîne. Si `end` est négatif, il est traité comme *longueur* + `end`. Si `end` est omis, copie continue jusqu'à la fin de `stringObj`. Si `end` se produit avant `start`, aucuns caractères ne sont copiés dans la nouvelle chaîne.  
  
## <a name="example"></a>Exemple  
 Dans le premier exemple, le `slice` méthode retourne la chaîne entière. Dans le deuxième exemple, la `slice` méthode retourne la chaîne entière, à l’exception du dernier caractère.  
  
```JavaScript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode slice (tableau)](../../javascript/reference/slice-method-array-javascript.md)