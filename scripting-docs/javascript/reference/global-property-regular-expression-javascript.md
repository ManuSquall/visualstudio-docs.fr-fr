---
title: "global, propriété (Regular Expression) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Global
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: global property
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e2b0256fea60b7ab998c504e79565fc7028cd98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="global-property-regular-expression-javascript"></a>global, propriété (Regular Expression) (JavaScript)
Retourne une valeur booléenne qui indique l’état de l’indicateur global (**g**) utilisé dans une expression régulière. Valeur par défaut est **false**. Lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
rgExp.global  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `rgExp` référence est une instance d’un **Expression régulière** objet.  
  
 Le `global` propriété renvoie **true** si l’indicateur global est défini pour une expression régulière et retourne **false** si elle n’est pas.  
  
 L’indicateur global, lorsqu’il est utilisé, indique qu’une recherche doit trouver toutes les occurrences du modèle dans la chaîne recherchée, pas seulement la première condition. On parle également de correspondance global.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `global` propriété. Si vous passez **g** dans à la fonction indiquée ci-dessous, toutes les instances du mot « the » sont remplacées par le mot « a ». Notez que l’instance « The » au début de la chaîne n’est pas remplacée car le **i** (ignorer la casse) indicateur n’est pas passé à la fonction.  
  
 Cette fonction affiche la condition des propriétés associées avec les indicateurs d’expression régulière autorisés, qui sont **g**, **i**, et **m**. La fonction affiche également la chaîne avec tous les remplacements effectués.  
  
```JavaScript  
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
  
## <a name="example"></a>Exemple  
 Voici le résultat obtenu.  
  
```JavaScript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S’applique aux**: [objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [IgnoreCase, propriété (Regular Expression)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [MultiLine, propriété (Regular Expression)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)