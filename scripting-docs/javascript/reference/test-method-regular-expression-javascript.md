---
title: "test, m&#233;thode (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "test"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "méthode de test"
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# test, m&#233;thode (Regular Expression) (JavaScript)
Retourne une valeur booléenne indiquant l'existence ou non d'un modèle dans une chaîne recherchée.  
  
## Syntaxe  
  
```  
  
rgExp.test(str)   
```  
  
## Paramètres  
 `rgExp`  
 Obligatoire.  Instance d'un objet **Regular Expression** contenant le modèle d'expression régulière et les indicateurs applicables.  
  
 `str`  
 Obligatoire.  Chaîne sur laquelle la recherche doit être effectuée.  
  
## Notes  
 La méthode **test** vérifie l'existence d'un modèle à l'intérieur d'une chaîne. Si le modèle existe, la méthode retourne la valeur **true** ; sinon, elle retourne la valeur **false**.  
  
 Les propriétés de l'objet `RegExp` global ne sont pas modifiées par la méthode **test**.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la méthode **test**.  Pour utiliser cet exemple, passez à la fonction un modèle d'expression régulière et une chaîne.  La fonction recherche alors le modèle d'expression régulière dans la chaîne et retourne une chaîne indiquant le résultat de cette recherche :  
  
```javascript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Voir aussi  
 [RegExp, objet](../../javascript/reference/regexp-object-javascript.md)   
 [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)