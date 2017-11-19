---
title: "Fill, méthode (Array) (JavaScript) | Documents Microsoft"
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4546bafb3fa3a8c242b8b7ef4ef2863ea86bf179
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="fill-method-array-javascript"></a>fill, méthode (Array) (JavaScript)
Remplit un tableau avec une valeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `arrayObj`  
 Obligatoire. Objet Array.  
  
 `value`  
 Obligatoire. Valeur utilisée pour remplir le tableau.  
  
 `start`  
 Facultatif. Index de départ utilisé pour remplir les valeurs de tableau. La valeur par défaut est 0.  
  
 `end`  
 Facultatif. Index de fin utilisé pour remplir les valeurs de tableau. La valeur par défaut est la propriété de longueur de l'objet `this`.  
  
## <a name="remarks"></a>Remarques  
 Si `start` est négatif, `start` est traité comme `length` + `start`, où `length` est la longueur du tableau. Si `end` est négatif, `end` est traité comme `length` + `end`.  
  
## <a name="example"></a>Exemple  
 Les exemples de code suivants remplissent un tableau avec des valeurs.  
  
```JavaScript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]