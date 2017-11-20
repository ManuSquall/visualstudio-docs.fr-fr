---
title: "DELETE, méthode (WeakMap) (JavaScript) | Documents Microsoft"
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd4cec06b77b7198e23d7e455849b5c0bf6d7ff9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-weakmap-javascript"></a>delete, méthode (WeakMap) (JavaScript)
Supprime l'élément spécifié d'un objet `WeakMap`.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
weakmapObj.delete(key)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `weakmapObj`  
 Obligatoire. Objet `WeakMap`.  
  
 `key`  
 Obligatoire. Clé de l'élément à supprimer.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 `true` si l'élément a été supprimé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment ajouter un membre à un `WeakMap` , puis supprimez-le.  
  
```JavaScript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]