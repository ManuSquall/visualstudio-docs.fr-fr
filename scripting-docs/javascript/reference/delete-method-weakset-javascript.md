---
title: DELETE, méthode (WeakSet) (JavaScript) | Documents Microsoft
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
ms.assetid: 19e93366-7d42-4abf-b7b9-fcf943fa17a3
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46eeac8ddd0072712c1867bc2a419a4e3255ffd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636289"
---
# <a name="delete-method-weakset-javascript"></a>delete, méthode (WeakSet) (JavaScript)
Supprime l'élément spécifié d'un `WeakSet`.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
weaksetObj.delete(obj)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `weaksetObj`  
 Obligatoire. Objet `WeakSet`.  
  
 `obj`  
 Obligatoire. Élément à supprimer.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 `true` si l'élément a été supprimé.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment ajouter et supprimer les éléments d'un `WeakSet`.  
  
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