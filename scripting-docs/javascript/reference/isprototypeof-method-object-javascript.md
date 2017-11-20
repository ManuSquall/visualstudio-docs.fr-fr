---
title: "isPrototypeOf, méthode (Object) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: isPrototypeOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: isPrototypeOf method
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47ce97faecfade089bbf0b7a725a02ee73b54718
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="isprototypeof-method-object-javascript"></a>isPrototypeOf, méthode (Object) (JavaScript)
Détermine si l'objet existe dans la chaîne prototype d'un autre objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## <a name="parameters"></a>Paramètres  
 `prototype`  
 Obligatoire. Un prototype d'objet.  
  
 `object`  
 Obligatoire. Autre objet dont la chaîne prototype est à vérifier.  
  
## <a name="remarks"></a>Remarques  
 La méthode `isPrototypeOf` retourne la valeur `true` si `object` a `prototype` dans sa chaîne prototype. La chaîne prototype est utilisée pour partager les fonctionnalités entre des instances d'un même type d'objet. La méthode `isPrototypeOf` retourne `false` si `object` n'est pas un objet ou si `prototype` n'apparaît pas dans la chaîne prototype d'`object`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `isPrototypeOf`.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)