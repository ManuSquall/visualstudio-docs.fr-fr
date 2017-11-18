---
title: "Add, méthode (WeakSet) (JavaScript) | Documents Microsoft"
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ab486beaba4a26c73930b5ceaee927f73aa077a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="add-method-weakset-javascript"></a>add, méthode (WeakSet) (JavaScript)
Ajoute un nouvel élément à `WeakSet`.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
weaksetObj.add(obj)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `weaksetObj`  
 Obligatoire. Objet `WeakSet`.  
  
 `obj`  
 Obligatoire. Nouvel élément de `WeakSet`.  
  
## <a name="remarks"></a>Remarques  
 Le nouvel élément doit être un objet, plutôt qu'une valeur arbitraire, et doit être unique. Si vous ajoutez un élément non unique à un `WeakSet`, le nouvel élément ne sera pas ajouté à la collection.  
  
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