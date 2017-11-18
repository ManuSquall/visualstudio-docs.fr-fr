---
title: "Get, méthode (WeakMap) (JavaScript) | Documents Microsoft"
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29decb7e6a050188b75639eb7cf4f27494b31da2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="get-method-weakmap-javascript"></a>get, méthode (WeakMap) (JavaScript)
Retourne un élément spécifié d’un `WeakMap` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
weakmapObj.get(key)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `weakmapObj`  
 Obligatoire. Objet `WeakMap`.  
  
 `key`  
 Obligatoire. La clé d’un élément dans le `WeakMap`.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Retourne l’objet associé à la clé. Si le `WeakMap` ne contient pas la clé, cette méthode retourne un `undefined` valeur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment récupérer des membres à partir d’un `WeakMap` objet.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]