---
title: "constructor, propriété (String) | Documents Microsoft"
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
ms.assetid: ef0e9c82-4651-4404-87b1-d00cad38c6f9
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f1942073a9950a77c7e0cae759a9653318d8a18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-string"></a>constructor, propriété (String)
Spécifie la fonction qui crée une chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
string.constructor  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `string` est le nom d’une chaîne.  
  
 La propriété `constructor` est un membre du prototype de chaque objet qui en possède un. Cela inclut toutes les intrinsèques [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] des objets à l’exception de la `Global` et `Math` objets. La propriété `constructor` contient une référence à la fonction qui crée les instances d'un objet donné.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la propriété de constructeur.  
  
```JavaScript  
var x = new String();  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
else  
    document.write("Object is not a String.");  
  
// Output:  
// Object is a String.  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]