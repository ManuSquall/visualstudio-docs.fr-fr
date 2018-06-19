---
title: IgnoreCase, propriété (Regular Expression) (JavaScript) | Documents Microsoft
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
- ignoreCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- IgnoreCase property
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae9fee8e6303fb944f59c11c173f9e8b7f7cc75a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637859"
---
# <a name="ignorecase-property-regular-expression-javascript"></a>ignoreCase, propriété (Regular Expression) (JavaScript)
Retourne une valeur booléenne qui indique l’état de l’indicateur ignoreCase (**i**) utilisé dans une expression régulière. Valeur par défaut est **false**. Lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
rgExp.ignoreCase  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `rgExp` référence est une instance de la `RegExp` objet.  
  
 Le **ignoreCase** propriété renvoie **true** si l’indicateur ignoreCase est défini pour une expression régulière et retourne **false** si elle n’est pas.  
  
 L’indicateur ignoreCase, lorsqu’il est utilisé, indique qu’une recherche doit ignorer la casse lors de la mise en correspondance le modèle dans la chaîne recherchée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **ignoreCase** propriété. Si vous passez « gi » à la fonction indiquée ci-dessous, toutes les instances du mot « the » sont remplacées par le mot « a », y compris l’initiale « The ». Il s’agit, car avec l’indicateur ignoreCase est défini, la recherche ne respecte pas la casse. Par conséquent, « T » est identique à « t » pour les besoins de mise en correspondance.  
  
 Cette fonction retourne les valeurs booléennes qui indiquent l’état des indicateurs d’expression régulière autorisés, qui sont **g**, **i**, et **m**. La fonction retourne également la chaîne avec tous les remplacements effectués.  
  
```JavaScript  
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
  
## <a name="example"></a>Exemple  
 Voici le résultat obtenu.  
  
```JavaScript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S’applique aux**: [objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [global, propriété (Regular Expression)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [MultiLine, propriété (Regular Expression)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)