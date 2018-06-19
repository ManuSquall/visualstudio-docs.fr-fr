---
title: arguments, objet (JavaScript) | Documents Microsoft
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
- arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments object
- arguments object
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a5c526d19ad5469d9d099f51cc5a2e2d089814f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634219"
---
# <a name="arguments-object-javascript"></a>arguments, objet (JavaScript)
Un objet représentant les arguments de la fonction en cours d’exécution, et les fonctions qui l’appellent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[function.]arguments[n]  
```  
  
## <a name="parameters"></a>Paramètres  
 *function*  
 Facultatif. Le nom d’en cours d’exécution `Function` objet.  
  
 *n*  
 Obligatoire. Index de base zéro aux valeurs d’argument passé à la `Function` objet.  
  
## <a name="remarks"></a>Remarques  
 Vous ne pouvez pas créer explicitement un **arguments** objet. Le **arguments** objet est disponible seulement quand une fonction lance l’exécution. Le **arguments** objet de la fonction n’est pas un tableau, mais les arguments individuels sont accessibles de la même façon que les éléments de tableau. L’index  *n*  est en fait une référence à un de la **0**  ***n***  propriétés de la **arguments** objet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **arguments** objet.  
  
```JavaScript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [0... n, propriétés (arguments)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [callee, propriété (arguments)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [Propriété length (arguments)](../../javascript/reference/length-property-arguments-javascript.md)