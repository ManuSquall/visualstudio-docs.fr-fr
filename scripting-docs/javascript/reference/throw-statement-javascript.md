---
title: throw, instruction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- throw_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error handling, throw statement
- throw statement
ms.assetid: 75cbade0-fb81-4ffe-b187-b71be380bb05
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cedecec1c5f13e1aba07273c1e3deca4f835429
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="throw-statement-javascript"></a>throw, instruction (JavaScript)
Génère une condition d’erreur qui peut être gérée par un `try...catch...finally` instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
throw exception   
```  
  
## <a name="remarks"></a>Remarques  
 Requis `exception` argument peut être n’importe quelle expression.  
  
 L’exemple suivant génère une erreur à l’intérieur d’un `try` bloc et elle est interceptée dans le `catch` bloc.  
  
```JavaScript  
try {  
        throw new Error(200, "x equals zero");  
}  
catch (e) {  
    document.write(e.message);  
}  
  
// Output: x equals zero.  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [try... catch... finally, instruction](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Objet Error](../../javascript/reference/error-object-javascript.md)