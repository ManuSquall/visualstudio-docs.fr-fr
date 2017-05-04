---
title: "Function, objet (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "function"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Function (objet)"
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Function, objet (JavaScript)
Crée une fonction.  
  
## Syntaxe  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## Syntaxe  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## Paramètres  
 `functionName`  
 Obligatoire.  Nom de la fonction dernièrement créée  
  
 `argname1...argnameN`  
 Facultatif.  Liste d'arguments acceptés par la fonction.  
  
 `body`  
 Facultatif.  Chaîne contenant le bloc de code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] à exécuter lors de l'appel de la fonction.  
  
## Notes  
 La fonction est un type de données de base dans [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  La syntaxe 1 crée une valeur de fonction que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convertit dans l'objet de `Function` si nécessaire.  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convertit les objets de `Function` créés par la syntaxe 2 en des valeurs de fonction, au moment de l'appel de la fonction.  
  
 La syntaxe 1 est le moyen standard de créer des fonctions dans [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  La syntaxe 2 est une autre forme utilisée pour créer des objets de fonction de façon explicite.  
  
 Par exemple, pour déclarer une fonction qui ajoute deux arguments passés à elle\-même, deux solutions sont possibles :  
  
## Exemple 1  
  
```javascript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## Exemple 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 Dans les deux cas, appelez la fonction avec une ligne de code similaire à celle\-ci :  
  
```javascript  
add(2, 3);  
```  
  
> [!NOTE]
>  Lors de l'appel d'une fonction, veillez à toujours inclure les parenthèses ainsi que les arguments requis.  L'omission des parenthèses lors de l'appel de la fonction provoque le retour de la fonction elle\-même, et non la valeur de retour de la fonction.  
  
## Propriétés  
 [0...  
          n, propriétés](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[arguments, propriété](../../javascript/reference/arguments-property-function-javascript.md) &#124; [callee, propriété](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [caller, propriété](../../javascript/reference/caller-property-function-javascript.md) &#124; [constructor, propriété](../../javascript/reference/constructor-property-object-javascript.md) &#124; [length, propriété \(Function\)](../../javascript/reference/length-property-function-javascript.md) &#124; [prototype, propriété](../../javascript/reference/prototype-property-object-javascript.md)  
  
## Méthodes  
 [apply, méthode](../../javascript/reference/apply-method-function-javascript.md) &#124; [bind, méthode](../../javascript/reference/bind-method-function-javascript.md) &#124; [call, méthode](../../javascript/reference/call-method-function-javascript.md) &#124; [toString, méthode](../../javascript/reference/tostring-method-object-javascript.md) &#124; [valueOf, méthode](../../javascript/reference/valueof-method-object-javascript.md)  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Voir aussi  
 [function, instruction](../../javascript/reference/function-statement-javascript.md)   
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Instruction var](../../javascript/reference/var-statement-javascript.md)