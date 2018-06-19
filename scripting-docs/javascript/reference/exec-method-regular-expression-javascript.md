---
title: EXEC, méthode (Regular Expression) (JavaScript) | Documents Microsoft
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
- exec
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- matching strings
- Exec method
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426cc1a8162b03090289cf737a03d64a75df77e9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637039"
---
# <a name="exec-method-regular-expression-javascript"></a>exec, méthode (Regular Expression) (JavaScript)
Exécute une recherche sur une chaîne à l’aide d’un modèle d’expression régulière et retourne un tableau contenant les résultats de recherche.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
rgExp.exec(str)   
```  
  
## <a name="parameters"></a>Paramètres  
 `rgExp`  
 Obligatoire. Une instance d’un **Expression régulière** objet qui contient le modèle d’expression régulière et les indicateurs applicables.  
  
 `str`  
 Obligatoire. Le `String` objet ou un littéral de chaîne sur laquelle effectuer la recherche.  
  
## <a name="remarks"></a>Remarques  
 Si le `exec` méthode ne trouve pas de correspondance, elle retourne `null`. S’il trouve une correspondance, `exec` retourne un tableau et les propriétés de l’élément global `RegExp` objet sont mis à jour pour refléter les résultats de la correspondance. L’élément zéro du tableau contient la correspondance entière, alors que les éléments 1 -  *n*  contiennent les sous-correspondances qui se sont produites dans la correspondance. Ce comportement est identique à celui de la `match` méthode sans l’indicateur global (**g**) défini.  
  
 Si l’indicateur global est défini pour une expression régulière, `exec` recherche la chaîne commençant à la position indiquée par la valeur de `lastIndex`. Si l’indicateur global n’est pas définie, `exec` ignore la valeur de `lastIndex` et les recherches à partir du début de la chaîne.  
  
 Le tableau retourné par la `exec` méthode possède trois propriétés, **d’entrée**, **index** et **lastIndex.** Le **d’entrée** propriété contient la totalité de la chaîne recherchée. Le **index** propriété contient la position de la sous-chaîne mise en correspondance dans la chaîne recherchée complète. Le `lastIndex` propriété contient la position suivant le dernier caractère de la correspondance.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `exec` méthode :  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [match, méthode (String)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp (objet)](../../javascript/reference/regexp-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Search, méthode (String)](../../javascript/reference/search-method-string-javascript.md)   
 [test, méthode (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programmation d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)