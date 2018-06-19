---
title: prototype, propriété (Set) | Documents Microsoft
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
ms.assetid: a075d5a6-e502-4636-85fc-1af001b8ac35
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8265d182562aee55f870fff4c3d5cbadf21402ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638859"
---
# <a name="prototype-property-set"></a>prototype, propriété (Set)
Retourne une référence au prototype pour un ensemble.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
set.prototype  
```  
  
## <a name="remarks"></a>Remarques  
 L'argument `set` est le nom d'un jeu.  
  
 Utilisez la propriété `prototype` pour fournir un ensemble de base de fonctionnalités à une classe d'objets. Les nouvelles instances d'un objet « héritent » du comportement du prototype attribué à cet objet.  
  
 Par exemple, pour ajouter une méthode à l'objet `Set` qui retourne la valeur de l'élément le plus grand de l'ensemble, déclarez la fonction, ajoutez-la à `Set.prototype`, puis utilisez-la.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]