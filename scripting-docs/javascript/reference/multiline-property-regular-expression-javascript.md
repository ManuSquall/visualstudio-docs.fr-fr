---
title: "multiline, propri&#233;t&#233; (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "multiline"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "multiline (propriété)"
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# multiline, propri&#233;t&#233; (Regular Expression) (JavaScript)
Retourne une valeur booléenne indiquant l'état de l'indicateur multiligne \(**m**\) utilisé dans une expression régulière.  La valeur par défaut est **false**.  Lecture seule.  
  
## Syntaxe  
  
```  
  
rgExp.multiline  
```  
  
## Notes  
 L'argument requis `rgExp` est une instance de l'objet de `RegExp`  
  
 La propriété **multiline** retourne la valeur **true** si l'indicateur multiligne est défini pour une expression régulière, et la valeur **false** dans le cas contraire.  La propriété **multiline** prend la valeur **true** si l'objet de l'expression régulière a été créé à l'aide de l'indicateur **m**.  
  
 Si la propriété **multiline** prend la valeur **false**, « ^ » correspond à la position en début de chaîne et « $ » à celle qui se trouve en fin de chaîne.  Si la propriété **multiline** a la valeur **true**, « ^ » correspond à la position en début de chaîne ainsi qu'à la position qui suit un caractère « \\n » ou « \\r ». Pour sa part, « $ » correspond à la position en fin de chaîne et à celle qui précède un caractère « \\n » ou « \\r ».  
  
## Exemple  
 L'exemple suivant illustre le comportement de la propriété **multiline** :  Si vous passez « m » à la fonction indiquée ci\-dessous, le mot « while » est remplacé par le mot « and ».  Cela est dû au fait que l'indicateur multiligne est défini et que le mot « while » figure au début de la ligne après un caractère de saut de ligne.  L'indicateur multiligne permet d'exécuter la recherche sur des chaînes multilignes.  
  
```javascript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S'applique à** : [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Voir aussi  
 [global, propriété \(Regular Expression\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [ignoreCase, propriété \(Regular Expression\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)