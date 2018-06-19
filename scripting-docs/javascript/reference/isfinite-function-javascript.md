---
title: isFinite, fonction (JavaScript) | Documents Microsoft
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
- isFinite
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- finite numbers
- isFinite method
ms.assetid: ea9287d2-892f-496b-86b7-f9196868d5cf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce78afe59190a03fb079841e7691f84c01eebedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636999"
---
# <a name="isfinite-function-javascript"></a>isFinite, fonction (JavaScript)
Détermine si un nombre fourni est fini.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
isFinite(number)   
```  
  
## <a name="remarks"></a>Remarques  
 Requis `number` argument est une valeur numérique.  
  
 Le `isFinite` fonction renvoie `true` si `number` est n’importe quelle valeur autre que `NaN`, l’infini négatif ou l’infini positif. Dans ces trois cas, elle retourne **false**.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S’applique aux**: [objet Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction isNaN](../../javascript/reference/isnan-function-javascript.md)