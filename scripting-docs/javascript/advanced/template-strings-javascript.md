---
title: "Cha&#238;nes de mod&#232;les (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Cha&#238;nes de mod&#232;les (JavaScript)
En [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)], vous pouvez utiliser des chaînes de modèles pour construire des littéraux de chaîne avec des expressions incorporées.  Les chaînes de modèles assurent également une prise en charge intégrée des chaînes de plusieurs lignes.  
  
 Pour construire une chaîne de modèle, utilisez l'accent grave \(\`\) des deux côtés de la chaîne à la place des guillemets simples ou doubles.  L'exemple de code suivant montre une chaîne de modèle simple.  
  
```  
`Template strings can include 'single quotes' and "double quotes" inline.`  
  
```  
  
 Les chaînes de modèles peuvent inclure des sauts de ligne sans nécessiter l'utilisation du caractère de saut de ligne \(\\n\).  
  
```  
`Template strings can include line breaks and don't need the linefeed character.`  
```  
  
 Le caractère $ est utilisé pour spécifier des espaces réservés dans une chaîne de modèle.  La syntaxe est ${*expression*}, où *expression* est n'importe quelle expression JavaScript comme une variable ou une fonction, comme indiqué dans l'exemple suivant.  
  
```  
var name = "Bob";  
var str = `Hello ${name}, how are you this fine ${partOfDay()}?`  
console.log(str);  
  
function partOfDay () {  
    var hour = new Date().getHours();  
  
    if (hours <= 12) {  
        return “morning”;  
    } else if (hours <= 5) {  
        return “afternoon”;  
    } else {  
        return “evening”;  
    }  
}  
  
// Output:  
// Hello Bob, how are you this fine afternoon?  
```  
  
 Les fonctions de modèle avec balises vous permettent de modifier la valeur d'une chaîne de modèle à l'aide d'une fonction appelée avec des arguments de la chaîne de modèle.  Le premier argument est un tableau de littéraux de chaîne, délimités par les expressions de chaîne de modèle qu'il contient, et le deuxième argument est un tableau \(un [paramètre rest](../../javascript/functions-javascript.md)\) qui contient les valeurs des expressions de chaîne de modèle.  
  
 Dans l'exemple suivant, la fonction de modèle avec balises, buildURL, est utilisée pour construire une URL.  La syntaxe consiste à utiliser le nom de fonction immédiatement suivi de la chaîne de modèle.  
  
```  
function buildURL(strArray, ...valArray) {  
    var newUrl = strArray[0] + "ja-ja" + "/" + valArray[1] +  
    "/" + valArray[2];  
  
    return newUrl;  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
console.log(url);  
  
// Output:  
// http://msdn.microsoft.com/ja-ja/library/dn771551.aspx  
```  
  
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
>  Vous pouvez également utiliser la fonction [String.raw](../../javascript/reference/string-raw-function-javascript.md) pour retourner la forme de chaîne brute d'une chaîne de modèle.  
  
## Voir aussi  
 [Informations de référence sur le langage JavaScript](../../javascript/javascript-language-reference.md)   
 [JavaScript avancé](../../javascript/advanced/advanced-javascript.md)