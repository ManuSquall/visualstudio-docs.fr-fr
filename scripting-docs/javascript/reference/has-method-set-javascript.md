---
title: has, méthode (Set) (JavaScript) | Documents Microsoft
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9690e3d091e8ae0f9670fd737a29590524834c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636719"
---
# <a name="has-method-set-javascript"></a>has, méthode (Set) (JavaScript)
Retourne `true` si le jeu contient l’élément spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
setObj.has(value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `setObj`  
 Obligatoire. Objet `Set`.  
  
 `value`  
 Obligatoire. Élément à tester.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 `true` si le jeu contient l'élément spécifié.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment ajouter des membres à un `Set`, puis vérifier si le jeu contient un membre spécifique.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]