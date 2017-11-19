---
title: "prototype, propriété (WeakMap) | Documents Microsoft"
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cc1bff0d62f2aeb8d6fb78a0857f287fb34078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-weakmap"></a>prototype, propriété (WeakMap)
Retourne une référence au prototype pour un `WeakMap` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
weakmap.prototype  
```  
  
## <a name="remarks"></a>Remarques  
 Le `weakmap` argument est le nom d’un `WeakMap` objet.  
  
 Utilisez la propriété `prototype` pour fournir un ensemble de base de fonctionnalités à une classe d'objets. Les nouvelles instances d'un objet « héritent » du comportement du prototype attribué à cet objet.  
  
 Par exemple, pour ajouter une méthode à la `WeakMap` objet qui retourne la valeur de l’élément le plus grand de la `WeakMap`, déclarez la fonction, ajoutez-la à `WeakMap.prototype`, puis l’utiliser.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]