---
title: Symbol.for, fonction (JavaScript) | Documents Microsoft
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b7e47c00fbaa321d71a3eeba79e523eee719fb2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="symbolfor-function-javascript"></a>Symbol.for, fonction (JavaScript)
Retourne le symbole d'une clé spécifiée ou, si la clé n'est pas présente, crée un objet symbole avec la nouvelle clé.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Symbol.for(key);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `key`  
 Obligatoire. Clé du symbole, également utilisée comme description.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode recherche le symbole dans le Registre des symboles globaux. Si vous sérialisez les symboles en tant que chaînes, utilisez le Registre des symboles globaux pour être certain qu'une chaîne particulière correspond au symbole approprié pour toutes les recherches.  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]