---
title: "match, méthode (String) (JavaScript) | Documents Microsoft"
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
- match
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Match method
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46727942d73779351f1c0cceaf2eb90a691a8ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="match-method-string-javascript"></a>match, méthode (String) (JavaScript)
Correspond à une chaîne avec une expression régulière et retourne un tableau contenant les résultats de recherche.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
stringObj.match(rgExp)   
```  
  
## <a name="parameters"></a>Paramètres  
 `stringObj`  
 Obligatoire. Le `String` objet ou un littéral de chaîne sur laquelle effectuer la recherche.  
  
 `rgExp`  
 Obligatoire. Un objet d’expression régulière qui contient le modèle d’expression régulière et les indicateurs applicables. Cela peut également être un nom de variable ou un littéral de chaîne contenant le modèle d’expression régulière et les indicateurs.  
  
## <a name="remarks"></a>Remarques  
 Si le `match` méthode ne trouve pas de correspondance, elle retourne `null`. S’il trouve une correspondance, `match` retourne un tableau et les propriétés de l’élément global `RegExp` objet sont mis à jour pour refléter les résultats de la correspondance.  
  
 Si l’indicateur global (`g`) n’est pas définie, élément zéro du tableau contient la correspondance entière, alors que les éléments 1 via  *n*  contiennent les sous-correspondances. Ce comportement est le même que le comportement de la [exec, méthode (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md) lorsque l’indicateur global n’est pas définie. Si l’indicateur global est défini, éléments 0-  *n*  contiennent toutes les correspondances qui s’est produite.  
  
 Si l’indicateur global n’est pas définie, le tableau retourné par la `match` méthode a deux propriétés, `input` et `index`. Le `input` propriété contient la totalité de la chaîne recherchée. Le `index` propriété contient la position de la sous-chaîne mise en correspondance dans la chaîne recherchée complète.  
  
 Si l’indicateur `i` est défini, la recherche ne respecte pas la casse.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `match`.  
  
```JavaScript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [EXEC, méthode (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [RegExp (objet)](../../javascript/reference/regexp-object-javascript.md)   
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Replace, méthode (String)](../../javascript/reference/replace-method-string-javascript.md)   
 [Search, méthode (String)](../../javascript/reference/search-method-string-javascript.md)   
 [test, méthode (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programmation d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternative et sous-expressions (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Références arrière (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)