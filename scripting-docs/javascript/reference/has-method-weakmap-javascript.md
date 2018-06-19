---
title: has, méthode (WeakMap) (JavaScript) | Documents Microsoft
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9a1706a1b96b5273ec280c4cef2be47a3bc6e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636689"
---
# <a name="has-method-weakmap-javascript"></a>has, méthode (WeakMap) (JavaScript)
Retourne `true` si le `WeakMap` objet contient l’élément spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
weakmapObj.has(key)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `weakmapObj`  
 Obligatoire. Objet `WeakMap`.  
  
 `key`  
 Obligatoire. La clé de l’élément à tester.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 `true`Si le `WeakMap` contient la clé spécifiée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment ajouter un membre à un `WeakMap` , puis utilisez `has` pour vérifier si elle est présente.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]