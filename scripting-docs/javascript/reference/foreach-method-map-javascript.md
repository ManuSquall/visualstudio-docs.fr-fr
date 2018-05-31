---
title: forEach, méthode (Map) (JavaScript) | Documents Microsoft
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 549d7d625fb4dfe88b2db69e6aa0ff66c7e90f66
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2018
ms.locfileid: "34335799"
---
# <a name="foreach-method-map-javascript"></a>forEach, méthode (Map) (JavaScript)
Exécute l’action spécifiée pour chaque élément dans un mappage.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Paramètres  
 `mapObj`  
 Obligatoire. Objet `Map`.  
  
 `callbackfn`  
 Obligatoire. La fonction qui `forEach` appelle une fois pour chaque élément dans le mappage. `callbackfn` accepte jusqu'à trois arguments. `forEach` appelle le `callbackfn` une fois pour chaque élément dans le mappage de fonction.  
  
 `thisArg`  
 Facultatif. Un objet qui le `this` mot clé peut faire référence au `callbackfn` (fonction). Si `thisArg` est omis, `undefined` est utilisé en tant que valeur `this`.  
  
## <a name="exceptions"></a>Exceptions  
 Si l'argument `callbackfn` n'est pas un objet de fonction, une exception `TypeError` est levée.  
  
## <a name="remarks"></a>Notes  
 La syntaxe de la fonction de rappel est la suivante :  
  
 `function callbackfn(value, key, mapObj)`  
  
 Vous pouvez déclarer la fonction de rappel à l’aide de trois paramètres, comme indiqué dans le tableau suivant.  
  
|Argument de rappel|Définition|  
|-----------------------|----------------|  
|`value`|Une valeur contenue dans le mappage.|  
|`key`|Une clé contenue dans la table.|  
|`mapObj`|Le `Map` objet à parcourir.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment récupérer les membres d’un `Map` à l’aide de `forEach`.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (value, key, mapObj) {  
    document.write(value.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]
