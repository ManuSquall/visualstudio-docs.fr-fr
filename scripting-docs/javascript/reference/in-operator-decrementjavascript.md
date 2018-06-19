---
title: in, opérateur (JavaScript) | Documents Microsoft
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
- in_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- in operator
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eefcd4c53d2e3366a26f0d8dfb099f59038507ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637449"
---
# <a name="in-operator-javascript"></a>in, opérateur (JavaScript)
Vérifie l'existence d'une propriété dans un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
result = property in object  
```  
  
## <a name="parameters"></a>Paramètres  
 `result`  
 Obligatoire. Toute variable.  
  
 `property`  
 Obligatoire. Une expression qui prend une expression de chaîne.  
  
 `object`  
 Obligatoire. N’importe quel objet.  
  
## <a name="remarks"></a>Remarques  
 Le `in` opérateur détermine si un objet possède une propriété nommée `property`. Il détermine également si la propriété fait partie de la chaîne de prototype de l’objet. Pour plus d’informations sur les prototypes d’objets, consultez [Prototypes et héritage de Prototype](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `in` opérateur :  
  
```JavaScript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)