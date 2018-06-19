---
title: Fonction Math.clz32 (JavaScript) | Documents Microsoft
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
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511f407acc327a32ed6c53c12283503e20b514fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638079"
---
# <a name="mathclz32-function-javascript"></a>Fonction Math.clz32 (JavaScript)
Retourne le nombre de zéros d'en-tête de la représentation binaire 32 bits d'un nombre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## <a name="remarks"></a>Remarques  
 Si `number` vaut 0, le résultat est 32. Si le bit le plus significatif de l'encodage binaire 32 bits de `number` est 1, le résultat est égal à 0.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **S’applique aux**: [Math (objet)](../../javascript/reference/math-object-javascript.md)