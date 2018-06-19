---
title: Get, méthode (Map) (JavaScript) | Documents Microsoft
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 243d5aa93289cb7a13b34567b7824d028151bad3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636449"
---
# <a name="get-method-map-javascript"></a>get, méthode (Map) (JavaScript)
Retourne un élément spécifié à partir d’une carte.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
mapObj.get(key)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `mapObj`  
 Obligatoire. Objet `Map`.  
  
 `key`  
 Obligatoire. La clé d’un élément dans le `Map`.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Retourne l’objet associé à la clé. Si le `Map` ne contient pas la clé, cette méthode retourne un `undefined` valeur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment récupérer un élément d’un `Map` objet.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]