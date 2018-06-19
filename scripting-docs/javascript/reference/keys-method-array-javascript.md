---
title: Keys, méthode (Array) (JavaScript) | Documents Microsoft
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
ms.assetid: fc5b6a30-642c-4bd7-ad31-a42667af2f3f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f600facc91dd10219196f580abd0f52537010dfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637419"
---
# <a name="keys-method-array-javascript"></a>keys, méthode (Array) (JavaScript)
Retourne un itérateur qui retourne les valeurs d'index du tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
arrayObj.keys();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `arrayObj`  
 Obligatoire. Objet Array.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment obtenir les valeurs de clés d'un tableau.  
  
```JavaScript  
var k = ["a", "b", "c"].keys();  
// k.next().value == 0  
// k.next().value == 1  
// k.next().value == 2   
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]