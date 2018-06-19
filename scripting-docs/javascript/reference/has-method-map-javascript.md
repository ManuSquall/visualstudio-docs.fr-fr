---
title: has, méthode (Map) (JavaScript) | Documents Microsoft
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48228b495c845bef91caa0b85e67980100a6f790
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636709"
---
# <a name="has-method-map-javascript"></a>has, méthode (Map) (JavaScript)
Retourne `true` si le mappage contient l’élément spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
mapObj.has(key)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `mapObj`  
 Obligatoire. Objet `Map`.  
  
 `key`  
 Obligatoire. La clé de l’élément à tester.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 `true`Si le mappage contient l’élément spécifié.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment ajouter un membre à un `Map` , puis vérifiez si la carte contient.  
  
```JavaScript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]