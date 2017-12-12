---
title: "Chaînes de modèles (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7b6aa430fd4f958c5519093b85d399060b6031a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="template-strings-javascript"></a>Chaînes de modèles (JavaScript)
En [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)], vous pouvez utiliser des chaînes de modèles pour construire des littéraux de chaîne avec des expressions incorporées. Les chaînes de modèles assurent également une prise en charge intégrée des chaînes de plusieurs lignes.  
  
 Pour construire une chaîne de modèle, utilisez l'accent grave (`) des deux côtés de la chaîne à la place des guillemets simples ou doubles. L'exemple de code suivant montre une chaîne de modèle simple.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Les chaînes de modèles peuvent inclure des sauts de ligne sans nécessiter l'utilisation du caractère de saut de ligne (\n).  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Le caractère $ est utilisé pour spécifier des espaces réservés dans une chaîne de modèle. La syntaxe est ${*expression*}, où *expression* est n’importe quelle expression JavaScript comme une variable ou une fonction, comme indiqué dans l’exemple suivant.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Les fonctions de modèle avec étiquettes vous permettent de modifier la valeur d’une chaîne de modèle à l’aide d’une fonction appelée avec des arguments de la chaîne de modèle. Le premier argument est un tableau de littéraux de chaîne, délimités par les expressions de chaîne de modèle qu’il contient, et le deuxième argument est un tableau (un [paramètre rest](../../javascript/functions-javascript.md)) qui contient les valeurs des expressions de chaîne de modèle.  
  
 Dans l’exemple suivant, la fonction de modèle avec étiquettes, buildURL, est utilisée pour construire une URL. La syntaxe consiste à utiliser le nom de fonction immédiatement suivi de la chaîne de modèle.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Si vous avez besoin d'accéder aux valeurs de chaînes brutes transmises, le premier argument passé à la fonction de modèle avec balises prend en charge une propriété `raw` qui retourne la forme de chaîne brute des chaînes transmises.  
  
```  
function buildURL(strArray, ...valArray) {  
    console.log(strArray.raw);  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
// Ouput:  
// http://msdn.microsoft.com/  
// /  
// en-us  
// library  
```  
  
> [!NOTE]
>  Vous pouvez également utiliser la fonction [String.raw](../../javascript/reference/string-raw-function-javascript.md) pour retourner la forme de chaîne brute d’une chaîne de modèle.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence sur le langage JavaScript](../../javascript/javascript-language-reference.md)   
 [JavaScript avancé](../../javascript/advanced/advanced-javascript.md)