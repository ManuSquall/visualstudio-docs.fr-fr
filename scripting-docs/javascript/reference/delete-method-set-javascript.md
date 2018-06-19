---
title: DELETE, méthode (Set) (JavaScript) | Documents Microsoft
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72762b93c6996fd72bd035c5d653f0e85f4ffd33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636089"
---
# <a name="delete-method-set-javascript"></a>delete, méthode (Set) (JavaScript)
Supprime l’élément spécifié à partir d’un jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
setObj.delete(value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `setObj`  
 Obligatoire. Objet `Set`.  
  
 `value`  
 Obligatoire. Élément à supprimer.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 `true` si l'élément a été supprimé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment ajouter des membres à un `Set` , puis supprimez un d'entre eux.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]