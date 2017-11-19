---
title: "constructor, propriété (Number) | Documents Microsoft"
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
ms.assetid: a348fe53-1b4a-42f5-964b-53d57342c906
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72679f55aef9b0ac8dc01794c7460dbd8cf0bdf8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-number"></a>constructor, propriété (Number)
Spécifie la fonction qui crée un nombre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
number.constructor  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `number` est le nom d’une chaîne.  
  
 La propriété `constructor` est un membre du prototype de chaque objet qui en possède un. Cela inclut toutes les intrinsèques [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] des objets à l’exception de la `Global` et `Math` objets. La propriété `constructor` contient une référence à la fonction qui crée les instances d'un objet donné.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la propriété de constructeur.  
  
```JavaScript  
var num = new Number();  
  
if (num.constructor == Number)  
    document.write("Object is a Number.");  
else  
    document.write("Object is not a Number.");  
  
// Output:  
// Object is a Number.  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]