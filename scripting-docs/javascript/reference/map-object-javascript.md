---
title: Mappage d’objet (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Map
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d89890f9fecaf61e47e136734ed7fefb7b73cabd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639289"
---
# <a name="map-object-javascript"></a>Map, objet (JavaScript)
Collection de paires clé/valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
mapObj = new Map()  
```  
  
## <a name="remarks"></a>Remarques  
 Les clés et valeurs dans la collection peuvent être de n’importe quel type. Si vous ajoutez une valeur à la collection à l'aide d'une clé existante, la nouvelle valeur remplace l'ancienne valeur.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Map`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[constructeur](../../javascript/reference/constructor-property-map.md)|Spécifie la fonction qui crée un mappage.|  
|[prototype](../../javascript/reference/prototype-property-map.md)|Retourne une référence au prototype pour une carte.|  
|[size](../../javascript/reference/size-property-map-javascript.md)|Retourne le nombre d’éléments dans un mappage.|  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Map`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|Supprime tous les éléments d’une carte.|  
|[supprimer](../../javascript/reference/delete-method-map-javascript.md)|Supprime un élément spécifié à partir d’une carte.|  
|[forEach](../../javascript/reference/foreach-method-map-javascript.md)|Exécute l’action spécifiée pour chaque élément dans un mappage.|  
|[get](../../javascript/reference/get-method-map-javascript.md)|Retourne un élément spécifié à partir d’une carte.|  
|[a](../../javascript/reference/has-method-map-javascript.md)|Retourne `true` si le mappage contient un élément spécifié.|  
|[set](../../javascript/reference/set-method-map-javascript.md)|Ajoute un élément à un mappage.|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|Retourne une représentation de chaîne d’un mappage.|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|Retourne la valeur primitive de l'objet spécifié.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment ajouter des membres à `Map`, puis les extraire.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
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