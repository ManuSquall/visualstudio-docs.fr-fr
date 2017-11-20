---
title: Math.Sign, fonction (JavaScript) | Documents Microsoft
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cae32118f2265e02c67592facff8e49e8edd633
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="mathsign-function-javascript"></a>Math.sign, fonction (JavaScript)
Retourne le signe d'un nombre indiquant si celui-ci est positif, négatif ou égal à 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Math.sign(number)  
```  
  
## <a name="remarks"></a>Remarques  
 L'argument `number` requis est une expression numérique pour laquelle le signe est nécessaire.  
  
 La valeur de retour est l'une des suivantes :  
  
-   `NaN`, si `number` est `NaN`.  
  
-   -0, si `number` est - 0.  
  
-   +0, si `number` est +0.  
  
-   -1, si `number` est négative et non - 0.  
  
-   +1, si `number` est positif et différent de +0.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]