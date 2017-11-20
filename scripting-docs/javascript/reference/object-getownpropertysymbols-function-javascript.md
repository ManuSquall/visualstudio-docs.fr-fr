---
title: Object.getownpropertysymbols, fonction (JavaScript) | Documents Microsoft
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bcddba77305e30e4c5ae13f6b1fc5c9385b7108
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertysymbols-function-javascript"></a>Object.getOwnPropertySymbols, fonction (JavaScript)
Retourne les symboles de propriété personnels d'un objet. Ces symboles sont ceux qui sont définis directement sur cet objet et non hérités du prototype de l'objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. Objet qui contient les symboles personnels.  
  
## <a name="return-value"></a>Valeur de retour  
 Tableau qui contient les symboles personnels de l'objet.  
  
## <a name="remarks"></a>Remarques  
 Vous devez utiliser `Object.getOwnPropertySymbols` pour obtenir les symboles de propriété d'un objet. `Object.getOwnPropertyNames` ne retourne pas les symboles de propriété.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment obtenir les symboles de propriété d'un objet.  
  
```JavaScript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]