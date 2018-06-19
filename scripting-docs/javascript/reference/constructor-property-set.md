---
title: constructor, propriété (Set) | Documents Microsoft
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
ms.assetid: f350b7eb-8994-40bf-9011-f8b20fcef34f
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea9af6d60c2ae8bc8a383c4cebbf0955e183895e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636209"
---
# <a name="constructor-property-set"></a>constructor, propriété (Set)
Spécifie la fonction qui crée un ensemble.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
set.constructor  
```  
  
## <a name="remarks"></a>Remarques  
 Le `set` requis est le nom du jeu.  
  
 La propriété `constructor` est un membre du prototype de chaque objet qui en possède un. Cela inclut tous les objets JavaScript intrinsèques, à l'exception des objets `Global` et `Math`. La propriété `constructor` contient une référence à la fonction qui crée les instances d'un objet donné.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]