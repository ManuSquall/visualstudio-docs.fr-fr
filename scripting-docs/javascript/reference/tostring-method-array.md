---
title: ToString, méthode (Array) | Documents Microsoft
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6dc7cbf843e47ffc2d21f5a2b1d03c43e675a130
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640409"
---
# <a name="tostring-method-array"></a>toString, méthode (Array)
Retourne une représentation d'un tableau sous forme de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array.toString()  
```  
  
## <a name="parameters"></a>Paramètres  
 `array`  
 Obligatoire. Le tableau pour représenter sous forme de chaîne.  
  
## <a name="return-value"></a>Valeur de retour  
 La représentation sous forme de chaîne du tableau.  
  
## <a name="remarks"></a>Remarques  
 Les éléments d’un `Array` sont convertis en chaînes. Les chaînes résultantes sont concaténées et séparées par des virgules.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **toString** méthode avec un tableau.  
  
```JavaScript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]