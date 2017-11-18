---
title: "Length, propriété (String) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], length
- Length property
- length property (String)
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 706a7f6986086f95613e09b9a8355eb5bc2702a7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-string-javascript"></a>length, propriété (String) (JavaScript)
Retourne la longueur d'un objet `String`.  
  
> [!WARNING]
>  Les chaînes JavaScript sont immuables, la longueur d’une chaîne ne peut pas être modifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## <a name="remarks"></a>Remarques  
 Le `length` propriété contient un entier qui indique le nombre de caractères dans le `String` objet. Le dernier caractère de la `String` objet a un index d’i`length` - 1.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser `length`. Les chaînes JavaScript sont immuables et ne peut pas être modifiées sur place. Toutefois, vous pouvez écrire la chaîne inversée dans un tableau et appeler `join` avec le caractère vide, ce qui produit une chaîne sans caractères de séparation.  
  
```JavaScript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]