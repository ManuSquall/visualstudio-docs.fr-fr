---
title: "boucle for.. d’instruction (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47154261fd4817ba95b8884bd6482a87e044a5a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="forof-statement-javascript"></a>for...of, instruction (JavaScript)
Exécute une ou plusieurs instructions pour chaque valeur d'un itérateur obtenu à partir d'un objet pouvant être itéré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Paramètres  
 `variable`  
 Obligatoire. Variable qui peut être toute valeur de propriété d'`object`.  
  
 `object`  
 Obligatoire. Un objet pouvant être itéré, comme un `Array`, `Map`, `Set`, ou un objet qui implémente le [interfaces d’itérateur](http://msdn.microsoft.com/en-us/3692355a-a703-4d43-8fb5-c03b4b7e8db1).  
  
 `statements`  
 Facultatif. Une ou plusieurs instructions à exécuter pour chaque valeur d'un `object`. Il peut s'agir d'une instruction composée.  
  
## <a name="remarks"></a>Remarques  
 Au début de chaque itération d'une boucle, la valeur de `variable` est la valeur de propriété suivante d'`object`.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de l'instruction `for...of` sur un tableau.  
  
```JavaScript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de l'instruction `for...of` sur un objet `Map`.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [instruction for... dans l’instruction](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instruction for](../../javascript/reference/for-statement-javascript.md)   
 [Instruction while](../../javascript/reference/while-statement-javascript.md)