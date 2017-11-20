---
title: "Join, méthode (Array) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: join
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Join method
- concatenating strings, join method
- arrays [Visual Studio], joining
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4591b12b3556384fef3e367d20cf9545d2f3dedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="join-method-array-javascript"></a>join, méthode (Array) (JavaScript)
Ajoute tous les éléments d’un tableau, séparés par la chaîne de séparateur spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
arrayObj.join([separator])   
```  
  
## <a name="parameters"></a>Paramètres  
 `arrayObj`  
 Obligatoire. Objet `Array`.  
  
 `separator`  
 Facultatif. Chaîne utilisée pour séparer un élément d’un tableau de l’élément suivant dans la boîte `String`. Si omis, les éléments du tableau sont séparés par des virgules.  
  
## <a name="remarks"></a>Remarques  
 Si un élément du tableau est **non défini** ou `null`, il est traité comme une chaîne vide.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **jointure** (méthode).  
  
```JavaScript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Objet String](../../javascript/reference/string-object-javascript.md)