---
title: valueOf, méthode (Array) | Documents Microsoft
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
ms.assetid: b694fe65-1297-4580-8af2-406932c06454
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68dc5599a495df42629ec49f25e8f5344f67e3d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640529"
---
# <a name="valueof-method-array"></a>valueOf, méthode (Array)
Retourne la valeur primitive de l'objet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array.valueOf()  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’a aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’instance de tableau.  
  
## <a name="remarks"></a>Remarques  
 Dans l’exemple suivant, l’objet instancié tableau est identique à la valeur de retour de cette méthode.  
  
```JavaScript  
var arr = [1, 2, 3, 4];  
var s = arr.valueOf();  
  
if (arr === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]