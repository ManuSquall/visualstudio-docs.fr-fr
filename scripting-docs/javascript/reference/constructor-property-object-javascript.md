---
title: "constructor, propriété (objet) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- constructor
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- constructor property
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 569dab69906aa167ef486923bd7ceb7455ac243e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-object-javascript"></a>constructor, propriété (Object) (JavaScript)
Spécifie la fonction qui crée un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.constructor  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `object` est le nom d’un objet ou une fonction.  
  
 La propriété `constructor` est un membre du prototype de chaque objet qui en possède un. Cela inclut toutes les intrinsèques [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] des objets à l’exception de la `Global` et `Math` objets. La propriété `constructor` contient une référence à la fonction qui crée les instances d'un objet donné.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la propriété de constructeur.  
  
```JavaScript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)