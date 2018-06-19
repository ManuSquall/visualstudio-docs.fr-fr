---
title: Object.Assign, fonction (Object) (JavaScript) | Documents Microsoft
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c156369299e58eac556d43a87476de2ce09173e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638819"
---
# <a name="objectassign-function-object-javascript"></a>Object.assign, fonction (Object) (JavaScript)
Copie les valeurs d'un ou de plusieurs objets sources dans un objet cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Object.assign(target, ...sources );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `target`  
 Obligatoire. Objet dans lequel les propriétés énumérables sont copiées.  
  
 `...sources`  
 Obligatoire. Un ou plusieurs objets à partir desquels les propriétés énumérables sont copiées.  
  
## <a name="exceptions"></a>Exceptions  
 Cette fonction génère une erreur `TypeError` dans le cas d'une erreur d'assignation, qui met fin à l'opération de copie. Une exception `TypeError` est levée si une propriété cible n'est pas accessible en écriture.  
  
## <a name="remarks"></a>Remarques  
 Cette fonction retourne l'objet cible. Uniquement *énumérable propre* les propriétés sont copiées à partir de l’objet source vers l’objet cible. Vous pouvez utiliser cette fonction pour fusionner ou cloner des objets.  
  
 Les sources `null` ou `undefined` sont traitées comme des objets vides et n'apportent rien à l'objet cible.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment fusionner un objet avec `Object.assign`.  
  
```JavaScript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment cloner un objet avec `Object.assign`.  
  
```JavaScript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]