---
title: Values, méthode (Array) (JavaScript) | Documents Microsoft
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
ms.assetid: b20699d6-f8b1-4744-8551-9e81c82850dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1a90dfd81ae8baf6590f69f0126adc97d42c20e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640689"
---
# <a name="values-method-array-javascript"></a>values, méthode (Array) (JavaScript)
Retourne un itérateur qui retourne les valeurs du tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
arrayObj.values();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `arrayObj`  
 Obligatoire. Objet Array.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment obtenir les valeurs d'un tableau.  
  
```JavaScript  
var v = ["a", "b", "c"].values();  
// v.next().value == "a"  
// v.next().value == "b"  
// v.next().value == "c"   
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]