---
title: "Compile, méthode (Regular Expression) (JavaScript) | Documents Microsoft"
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
- compile
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- regular expressions, compiling
- Compile method
- compiling source code, regular expressions
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b8de23a9e4f0e03fbf042195867ad9426e4c6bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="compile-method-regular-expression-javascript"></a>compile, méthode (Regular Expression) (JavaScript)
Compile une expression régulière en un format interne pour une exécution plus rapide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## <a name="parameters"></a>Paramètres  
 `rgExp`  
 Obligatoire. Une instance d’un **Expression régulière** objet. Peut être un nom de variable ou un littéral.  
  
 *modèle*  
 Obligatoire. Une expression de chaîne contenant un modèle d’expression régulière à compiler  
  
 `flags`  
 Facultatif. Les indicateurs disponibles, qui peuvent être combinés, sont :  
  
-   g (recherche globale de toutes les occurrences de *modèle*)  
  
-   i (ignorer la casse)  
  
-   m (recherche multiligne)  
  
## <a name="remarks"></a>Remarques  
 Le **compiler** méthode convertit *modèle* dans un format interne pour une exécution plus rapide. Cela permet une utilisation plus efficace des expressions régulières dans les boucles, par exemple. Une expression régulière compilée accélère choses lors de la réutilisation de la même expression à plusieurs reprises. Ne présente aucun avantage n’est en revanche, si l’expression régulière est modifié.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **compiler** méthode :  
  
```JavaScript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)