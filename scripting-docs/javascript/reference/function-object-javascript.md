---
title: "Fonction d’objet (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: function
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Function object
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4392fd57967e6312c96af50bdff2415d0f2dcd4d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="function-object-javascript"></a>Function, objet (JavaScript)
Crée une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## <a name="parameters"></a>Paramètres  
 `functionName`  
 Obligatoire. Le nom de la fonction qui vient d’être créé.  
  
 `argname1...argnameN`  
 Facultatif. Une liste d’arguments de que la fonction accepte.  
  
 `body`  
 Facultatif. Chaîne qui contient le bloc de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] code à exécuter lorsque la fonction est appelée.  
  
## <a name="remarks"></a>Remarques  
 La fonction est un type de données de base dans [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. La syntaxe 1 crée une valeur de fonction qui [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convertit en un `Function` de l’objet lorsque cela est nécessaire. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Convertit `Function` objets créés par la syntaxe 2 en valeurs de fonction au moment de l’appel de la fonction.  
  
 La syntaxe 1 est le moyen standard de créer de nouvelles fonctions dans [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. La syntaxe 2 est une autre forme permet de créer explicitement des objets de fonction.  
  
 Par exemple, pour déclarer une fonction qui ajoute les deux arguments qui lui est passés, vous pouvez le faire de deux manières :  
  
## <a name="example-1"></a>Exemple 1  
  
```JavaScript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## <a name="example-2"></a>Exemple 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 Dans les deux cas, vous appelez la fonction avec une ligne de code semblable au suivant :  
  
```JavaScript  
add(2, 3);  
```  
  
> [!NOTE]
>  Lorsque vous appelez une fonction, assurez-vous que vous incluez toujours les parenthèses et tous les arguments requis. La fonction elle-même à retourner, au lieu de la valeur de retour de la fonction provoque l’appel d’une fonction sans parenthèses.  
  
## <a name="properties"></a>Propriétés  
 [0... n, propriétés](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[ arguments, propriété](../../javascript/reference/arguments-property-function-javascript.md) &#124; [callee, propriété](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [caller, propriété](../../javascript/reference/caller-property-function-javascript.md) &#124; [constructor, propriété](../../javascript/reference/constructor-property-object-javascript.md) &#124; [length, propriété (Function)](../../javascript/reference/length-property-function-javascript.md) &#124; [prototype, propriété](../../javascript/reference/prototype-property-object-javascript.md)  
  
## <a name="methods"></a>Méthodes  
 [Méthode Apply](../../javascript/reference/apply-method-function-javascript.md) &#124; [méthode bind](../../javascript/reference/bind-method-function-javascript.md) &#124; [appeler la méthode](../../javascript/reference/call-method-function-javascript.md) &#124; [ToString, méthode](../../javascript/reference/tostring-method-object-javascript.md) &#124; [valueOf, méthode](../../javascript/reference/valueof-method-object-javascript.md)  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction Function](../../javascript/reference/function-statement-javascript.md)   
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Instruction var](../../javascript/reference/var-statement-javascript.md)