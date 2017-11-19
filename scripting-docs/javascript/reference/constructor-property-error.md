---
title: "constructor, propriété (Error) | Documents Microsoft"
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
ms.assetid: 18aea278-2bd5-457b-83a5-d8d8f1226e0c
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1ade0ab1ba771b2ff9dfb7051b2983b3da77ed4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-error"></a>constructor, propriété (Error)
Spécifie la fonction qui crée une erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
error.constructor  
```  
  
## <a name="remarks"></a>Remarques  
 Requis `error` est le nom d’un objet d’erreur.  
  
 La propriété `constructor` est un membre du prototype de chaque objet qui en possède un. La propriété `constructor` contient une référence à la fonction qui crée les instances d'un objet donné.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la propriété de constructeur.  
  
```JavaScript  
var x = new Error("This is an error");  
  
if (x.constructor == Error)  
    document.write("Object is an error.");  
  
// Output:  
// Object is an error.  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]