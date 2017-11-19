---
title: Weakset, objet (JavaScript) | Documents Microsoft
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
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e42849c03f698d6ed5f8b0e28725c85555a74d2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="weakset-object-javascript"></a>WeakSet, objet (JavaScript)
Une collection d’objets uniques peut être de n’importe quel type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
setObj = new WeakSet()  
```  
  
## <a name="remarks"></a>Remarques  
 Si vous essayez d'ajouter un objet non unique à un `WeakSet`, le nouvel objet ne sera pas ajouté à la collection.  
  
 Contrairement à un `Set`, seuls les objets peuvent être ajoutés à la collection. Les valeurs arbitraires ne peuvent pas être ajoutés à la collection.  
  
 Dans un `WeakSet` de l’objet, les références aux objets dans le jeu sont conservées « faiblement ». Cela signifie que `WeakSet` n'empêchera pas un garbage collection de se produire sur les objets. Lorsqu'il n'y a aucune référence (autre que `WeakSet`) pour les objets, le garbage collector peut collecter les objets.  
  
 `WeakSet` (ou `WeakMap`) peut être utile dans certains scénarios impliquant la mise en cache des objets ou des métadonnées des objets. Par exemple, les métadonnées des objets non extensibles peuvent être stockées dans un `WeakSet`, ou vous pouvez créer un cache d'images d'utilisateur à l'aide de `WeakSet`.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `WeakSet`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|constructeur|Spécifie la fonction qui crée un ensemble.|  
|prototype|Retourne une référence au prototype pour un ensemble.|  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `WeakSet`.  
  
|Méthode|Description|  
|------------|-----------------|  
|add|Ajoute un élément à un ensemble.|  
|delete|Supprime un élément spécifié d'un ensemble.|  
|has|Retourne `true` si l'ensemble contient l'élément spécifié.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment ajouter des membres à un ensemble, puis vérifier qu'ils ont été ajoutés.  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]