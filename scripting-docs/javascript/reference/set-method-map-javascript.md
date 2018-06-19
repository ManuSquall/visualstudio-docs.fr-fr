---
title: Set, méthode (Map) (JavaScript) | Documents Microsoft
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a84a5b2714fde55fba03d581faa851d7245e001
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639429"
---
# <a name="set-method-map-javascript"></a>set, méthode (Map) (JavaScript)
Ajoute un élément à un mappage.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
mapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `mapObj`  
 Obligatoire. Objet `Map`.  
  
 `key`  
 Obligatoire. Clé du nouvel élément.  
  
 `value`  
 Obligatoire. Valeur de l'élément à ajouter.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Retourne l'objet `Map` qui contient la nouvelle paire clé/valeur.  
  
## <a name="remarks"></a>Remarques  
 Si vous ajoutez une valeur à la collection à l’aide d’une clé existante, la nouvelle valeur remplace l’ancienne valeur.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment ajouter des membres à `Map`, puis les extraire.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]