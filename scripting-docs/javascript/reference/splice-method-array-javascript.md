---
title: splice, méthode (Array) (JavaScript) | Documents Microsoft
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
- splice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- splice method
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d56a22244f76f5ce7221c276629907811733d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639559"
---
# <a name="splice-method-array-javascript"></a>splice, méthode (Array) (JavaScript)
Supprime les éléments d'un tableau et, si nécessaire, insère de nouveaux éléments à leur place, tout en retournant les éléments supprimés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## <a name="parameters"></a>Paramètres  
 `arrayObj`  
 Obligatoire. Objet `Array`.  
  
 `start`  
 Obligatoire. Emplacement de base zéro dans le tableau à partir duquel commencer la suppression d’éléments.  
  
 `deleteCount`  
 Obligatoire. Nombre d'éléments à supprimer.  
  
 `item1, item2,. . ., itemN`  
 Facultatif. Éléments à insérer dans le tableau à la place les éléments supprimés.  
  
## <a name="remarks"></a>Remarques  
 Le `splice` méthode modifie `arrayObj` en supprimant le nombre spécifié d’éléments à partir de la position `start` et l’insertion de nouveaux éléments. Les éléments supprimés sont retournés en tant que nouvelle `Array` objet.  
  
## <a name="example"></a>Exemple  
 Le code suivant met en œuvre la méthode `splice`.  
  
```JavaScript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode slice (tableau)](../../javascript/reference/slice-method-array-javascript.md)