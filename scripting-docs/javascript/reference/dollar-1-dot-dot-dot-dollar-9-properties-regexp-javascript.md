---
title: "$1... $9, propriétés (RegExp) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: $1...$9
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: $1...$9 properties
ms.assetid: 8bd84851-f62f-4eb1-a93d-b67135ea091a
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1926d6281c9003c432c9c9e89a73a48a584ef4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="19-properties-regexp-javascript"></a>$1...$9, propriétés (RegExp) (JavaScript)
Retourner que les neuf derniers sous-chaînes trouvé lors de la recherche de correspondance. Lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RegExp.$n   
```  
  
## <a name="parameters"></a>Paramètres  
 `RegExp`  
 Toujours global `RegExp` objet.  
  
 `n`  
 Tout entier compris entre 1 et 9.  
  
## <a name="remarks"></a>Remarques  
 Les valeurs de la **$1... $9** propriétés sont modifiées lors d’une correspondance entre parenthèses. Un nombre quelconque de sous-chaînes entre parenthèses peut être spécifié dans un modèle d’expression régulière, mais seules les neuf plus récentes peuvent être stockées.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant effectue une recherche d’expression régulière. Il affiche des correspondances et submatches à partir de la liste globale `RegExp` objet. Les sous-correspondances sont des correspondances entre parenthèses qui figurent dans le `$1...$9` propriétés. L’exemple affiche les correspondances également et submatches à partir du tableau retourné par la `exec` (méthode).  
  
```JavaScript  
var newLine = "<br />";  
  
var re = /(\w+)@(\w+)\.(\w+)/g  
var src = "Please send mail to george@contoso.com and someone@example.com. Thanks!"  
  
var result;  
var s = "";  
  
// Get the first match.  
result = re.exec(src);  
  
while (result != null) {  
    // Show the entire match.  
    s += newLine;  
  
    // Show the match and submatches from the RegExp global object.  
    s += "RegExp.lastMatch: " + RegExp.lastMatch + newLine;  
    s += "RegExp.$1: " + RegExp.$1 + newLine;  
    s += "RegExp.$2: " + RegExp.$2 + newLine;  
    s += "RegExp.$3: " + RegExp.$3 + newLine;  
  
    // Show the match and submatches from the array that is returned  
    // by the exec method.  
    for (var index = 0; index < result.length; index++) {  
        s +=  index + ": ";  
        s += result[index];  
        s += newLine;  
    }  
  
    // Get the next match.  
    result = re.exec(src);  
}  
document.write(s);  
  
// Output:  
//  RegExp.lastMatch: george@contoso.com  
//  RegExp.$1: george  
//  RegExp.$2: contoso  
//  RegExp.$3: com  
//  0: george@contoso.com  
//  1: george  
//  2: contoso  
//  3: com  
  
//  RegExp.lastMatch: someone@example.com  
//  RegExp.$1: someone  
//  RegExp.$2: example  
//  RegExp.$3: com  
//  0: someone@example.com  
//  1: someone  
//  2: example  
//  3: com  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [RegExp (objet)](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)