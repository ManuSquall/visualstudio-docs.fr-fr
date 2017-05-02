---
title: "global, propri&#233;t&#233; (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "Global"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "global (propriété)"
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# global, propri&#233;t&#233; (Regular Expression) (JavaScript)
Retourne une valeur booléenne indiquant l'état de l'indicateur global \(**g**\) utilisé dans une expression régulière.  La valeur par défaut est **false**.  Lecture seule.  
  
## Syntaxe  
  
```  
  
rgExp.global  
```  
  
## Notes  
 La référence `rgExp` requise est une instance d'un objet **Regular Expression**.  
  
 La propriété `global` retourne la valeur **true** si l'indicateur global est défini pour une expression régulière, ou la valeur **false** dans le cas contraire.  
  
 L'indicateur global, lorsqu'il est utilisé, indique qu'une recherche doit trouver toutes les occurrences du modèle spécifié dans la chaîne recherchée, et non pas uniquement la première.  Cette opération est également connue sous le nom de correspondance globale.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la propriété `global`.  Si vous passez **g** à la fonction indiquée ci\-dessous, toutes les instances du mot « the » sont remplacées par le mot « a ».  Notez que l'instance « The » figurant au début de la chaîne n'est pas remplacée car l'indicateur **i** \(ignorer la casse\) n'est pas passé à la fonction.  
  
 Cette fonction affiche la condition des propriétés associées aux indicateurs d'expression régulière autorisés, qui sont **g**, **i** et **m**.  La fonction affiche également la chaîne dans laquelle tous les remplacements ont été effectués.  
  
```javascript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## Exemple  
 Le résultat se présente comme suit :  
  
```javascript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S'applique à** : [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Voir aussi  
 [ignoreCase, propriété \(Regular Expression\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [multiline, propriété \(Regular Expression\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)