---
title: prototype, propriété (WeakSet) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 950e15a2-2f56-4cb9-8e48-020efd97f938
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c66c7854a83dcf3128025350a7fcdd17f4dfaf5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639159"
---
# <a name="prototype-property-weakset"></a>prototype, propriété (WeakSet)
Retourne une référence au prototype pour un `WeakSet`.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
weakset.prototype  
```  
  
## <a name="remarks"></a>Remarques  
 L'argument `weakset` est le nom d'un jeu.  
  
 Utilisez la propriété `prototype` pour fournir un ensemble de base de fonctionnalités à une classe d'objets. Les nouvelles instances d'un objet « héritent » du comportement du prototype attribué à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `WeakSet` qui retourne la valeur de l'élément le plus grand de l'ensemble, déclarez la fonction, ajoutez-la à `WeakSet.prototype`, puis utilisez-la.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]