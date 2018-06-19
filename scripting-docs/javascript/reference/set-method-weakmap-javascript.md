---
title: Set, méthode (WeakMap) (JavaScript) | Documents Microsoft
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c916bda13c7bd973b37c4e4cb6b81e327ee5de54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639599"
---
# <a name="set-method-weakmap-javascript"></a>set, méthode (WeakMap) (JavaScript)
Ajoute un nouvel élément à un objet `WeakMap`.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
weakmapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `weakmapObj`  
 Obligatoire. Objet `WeakMap`.  
  
 `key`  
 Obligatoire. Objet représentant la clé de l'élément à ajouter. Ce doit être une référence d'objet .  
  
 `value`  
 Obligatoire. Valeur de l'élément à ajouter.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Retourne l'objet `WeakMap` qui contient la nouvelle paire clé/valeur.  
  
## <a name="remarks"></a>Remarques  
 Si vous ajoutez une valeur à la collection à l’aide d’une clé existante, la nouvelle valeur remplace l’ancienne valeur.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment ajouter des membres à un objet `WeakMap`.  
  
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
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]