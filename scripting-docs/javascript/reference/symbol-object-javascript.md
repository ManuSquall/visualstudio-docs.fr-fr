---
title: "Symbole d’objet (JavaScript) | Documents Microsoft"
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
ms.assetid: 2ad059f1-4b7f-4758-882a-c74ce1283ab0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd755d5b753eb91b89b869645287685a97f8f571
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="symbol-object-javascript"></a>Symbol, objet (JavaScript)
Permet de créer un identificateur unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
obj = Symbol(desc)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `desc`  
 Facultatif. Description du symbole.  
  
## <a name="remarks"></a>Remarques  
 Les objets symbole permettent d'ajouter des propriétés à un objet existant sans risque d’interférence avec les siennes propres, sans visibilité involontaire, et sans ajout non coordonné par un autre code.  
  
 Symbole est un type de données primitif. Les objets symbole ne peuvent pas être créés à l'aide de l'opérateur `new`.  
  
 Pour ajouter des objets symbole au Registre des symboles globaux, utilisez les fonctions `Symbol.for` et `Symbol.keyFor`. Si vous sérialisez les symboles en tant que chaînes, utilisez le Registre des symboles globaux pour être certain qu'une chaîne particulière correspond au symbole approprié pour toutes les recherches.  
  
 JavaScript inclut les valeurs de symbole intégrées suivantes, lesquelles sont disponibles dans la portée globale.  
  
|Symbole|Description|  
|------------|-----------------|  
|`Symbol.hasInstance`|Cette méthode détermine si un objet constructeur reconnaît un objet en tant qu’une des instances du constructeur. Il est utilisé en interne par l'opérateur `instanceof`.|  
|`Symbol.isConcatSpreadable`|Cette propriété retourne une valeur booléenne qui indique si un objet doit être aplati à ses éléments de tableau par `Array.concat`.|  
|`Symbol.iterator`|Cette méthode retourne l'itérateur par défaut pour un objet. Il est utilisé en interne par l'instruction `for...of`.|  
|`Symbol.toPrimitive`|Cette méthode convertit un objet en valeur primitive correspondante. Elle est utilisée en interne par l'opérateur abstraite `ToPrimitive`.|  
|`Symbol.toStringTag`|Cette propriété retourne une valeur de chaîne qui est utilisée pour créer la description de chaîne par défaut d'un objet. Elle est utilisée en interne par la méthode intégrée `Object.toString`.|  
|`Symbol.unscopables`|Cette propriété retourne un objet dont les propriétés sont exclues des liaisons d'environnement `with` de l'objet associé.|  
  
## <a name="functions"></a>Fonctions  
 Le tableau suivant répertorie les fonctions de l'objet `Symbol`.  
  
|||  
|-|-|  
|Propriété|Description|  
|[Symbol.for](../../javascript/reference/symbol-for-function-javascript.md)|Retourne le symbole d'une clé spécifiée ou, si la clé n'est pas présente, crée un objet symbole avec la nouvelle clé.|  
|[Symbol.keyFor](../../javascript/reference/symbol-keyfor-function-javascript.md)|Retourne la clé d'un symbole spécifié.|  
|||  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
(function() {  
  
    // module-scoped symbol  
    var key = Symbol("description");  
  
    function MyClass(privateData) {  
      this[key] = privateData;  
    }  
  
    MyClass.prototype = {  
      someFunc: function() {  
        return "data: " + this[key];  
      }  
    };  
  
    var c = new MyClass("private data")  
    console.log(key);  
    console.log(c["key"]);  
    console.log(c.someFunc());  
  
})();  
  
// Output:  
// undefined  
// undefined  
// data: private data  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]