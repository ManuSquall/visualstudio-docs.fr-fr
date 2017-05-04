---
title: "ignoreCase, propri&#233;t&#233; (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "ignoreCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ignoreCase (propriété)"
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# ignoreCase, propri&#233;t&#233; (Regular Expression) (JavaScript)
Retourne une valeur booléenne indiquant l'état de l'indicateur ignoreCase \(**i**\) utilisé dans une expression régulière.  La valeur par défaut est **false**.  Lecture seule.  
  
## Syntaxe  
  
```  
  
rgExp.ignoreCase  
```  
  
## Notes  
 La référence `rgExp` requise est une instance de l'objet `RegExp`.  
  
 La propriété **ignoreCase** retourne la valeur **true** si l'indicateur ignoreCase est défini pour une expression régulière, et la valeur **false** dans le cas contraire.  
  
 L'indicateur ignoreCase, lorsqu'il est utilisé, précise qu'une recherche ne doit pas faire la distinction entre les majuscules et les minuscules lors de la comparaison avec le modèle dans la chaîne recherchée.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la propriété **ignoreCase**.  Si vous passez « gi » à la fonction indiquée ci\-dessous, toutes les instances du mot « the » sont remplacées par le mot « a », y compris l'instance initiale « The ».  En effet, lorsque l'indicateur ignoreCase est défini, la recherche ne tient pas compte de la casse.  Par conséquent, « T » est identique à « t » en termes de correspondance.  
  
 Cette fonction retourne les valeurs booléennes indiquant l'état des indicateurs d'expression régulière autorisés, qui sont **g**, **i** et **m**.  La fonction retourne également la chaîne dans laquelle tous les remplacements ont été effectués.  
  
```javascript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## Exemple  
 Le résultat se présente comme suit :  
  
```javascript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S'applique à** : [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Voir aussi  
 [global, propriété \(Regular Expression\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [multiline, propriété \(Regular Expression\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)