---
title: Add, méthode (Set) (JavaScript) | Documents Microsoft
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 287dbfb6480289ed57edc26d41e9900e4a76c27b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633169"
---
# <a name="add-method-set-javascript"></a>add, méthode (Set) (JavaScript)
Ajoute un élément à un ensemble.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
setObj.add(value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `setObj`  
 Obligatoire. Objet `Set`.  
  
 `value`  
 Obligatoire. Nouvel élément de `Set`.  
  
## <a name="remarks"></a>Remarques  
 Le nouvel élément peut être de n'importe quel type et doit être unique. Si vous ajoutez un élément non unique à un `Set`, le nouvel élément ne sera pas ajouté à la collection.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment ajouter des membres à un ensemble, puis les extraire.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]