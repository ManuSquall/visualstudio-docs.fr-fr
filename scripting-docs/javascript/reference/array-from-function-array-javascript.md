---
title: Array.From, fonction (Array) (JavaScript) | Documents Microsoft
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
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a240cb439942bfeb6b4c9a1febb4d24cef1c5c18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="arrayfrom-function-array-javascript"></a>Array.from, fonction (Array) (JavaScript)
Retourne un tableau à partir d'un objet de type tableau ou pouvant être itéré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `arrayLike`  
 Obligatoire. Objet de type tableau ou pouvant être itéré.  
  
 `mapfn`  
 Facultatif. Fonction de mappage à appeler sur chaque élément dans `arrayLike`.  
  
 `thisArg`  
 Facultatif. Spécifie l'objet `this` dans la fonction de mappage.  
  
## <a name="remarks"></a>Remarques  
 Le paramètre `arrayLike` doit être un objet avec des éléments indexés et une propriété `length` ou un objet pouvant être itéré, comme un objet `Set`.  
  
 La fonction de mappage facultative est appelée sur chaque élément du tableau.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne un tableau à partir d’une collection de nœuds d’éléments DOM.  
  
```JavaScript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant retourne un tableau de caractères.  
  
```JavaScript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne un tableau d’objets contenus dans la collection.  
  
```JavaScript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";   
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la syntaxe de fonction Arrow et d'une fonction de mappage pour modifier la valeur des éléments.  
  
```JavaScript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]