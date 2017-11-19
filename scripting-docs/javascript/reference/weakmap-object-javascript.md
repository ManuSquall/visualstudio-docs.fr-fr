---
title: WeakMap, objet (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: WeakMap
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8de97f8acb94921090696e9019a1df5d945db7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="weakmap-object-javascript"></a>WeakMap, objet (JavaScript)
Collection de paires clé/valeur dans laquelle chaque clé est une référence d’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
weakmapObj = new WeakMap()  
```  
  
## <a name="remarks"></a>Remarques  
 A `WeakMap` objet ne peut pas être énuméré.  
  
 Si vous ajoutez une valeur à la collection à l’aide d’une clé existante, la nouvelle valeur remplace l’ancienne valeur.  
  
 Dans un `WeakMap` de l’objet, les références aux objets clés sont conservées « faiblement ». Cela signifie que `WeakMap` n’empêchera pas un garbage collection de se produire sur les objets clés. Lorsqu’il y a aucune référence (autre que `WeakMap`) pour les objets de clé, le garbage collector peut collecter les objets clés.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `WeakMap`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[constructeur](../../javascript/reference/constructor-property-weakmap.md)|Spécifie la fonction qui crée un `WeakMap`.|  
|[prototype](../../javascript/reference/prototype-property-weakmap.md)|Retourne une référence au prototype pour un `WeakMap`.|  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `WeakMap`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|Supprime tous les éléments d'une `WeakMap`.|  
|[supprimer](../../javascript/reference/delete-method-weakmap-javascript.md)|Supprime un élément spécifié d’un `WeakMap`.|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|Retourne un élément spécifié d’un `WeakMap`.|  
|[a](../../javascript/reference/has-method-weakmap-javascript.md)|Retourne `true` si le `WeakMap` contient un élément spécifié.|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|Ajoute un nouvel élément à `WeakMap`.|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|Retourne une représentation sous forme de chaîne d’un `WeakMap`.|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|Retourne la valeur primitive de l'objet spécifié.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment ajouter des membres à un `WeakMap` de l’objet, puis les extraire.  
  
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