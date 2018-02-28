---
title: "__proto_, propriété (objet) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __proto__
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e38669c400acba6f4ed3c4ee3fb5836c31b1bc00
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="proto-property-object-javascript"></a>__proto__ , propriété (objet) (JavaScript)
Contient une référence au prototype interne de l’objet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
object.__proto__  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. L’objet sur lequel définir le prototype.  
  
## <a name="remarks"></a>Remarques  
 Le `__proto__` propriété peut être utilisée pour définir le prototype pour un objet.  
  
 L’objet ou une fonction hérite de toutes les méthodes et propriétés du nouveau prototype, ainsi que toutes les méthodes et propriétés dans la chaîne de prototype du nouveau prototype. Un objet peut avoir uniquement un prototype unique (sans les prototypes hérités dans la chaîne prototype), par conséquent, lorsque vous appelez le `__proto__` propriété, vous remplacez le prototype de la précédent.  
  
 Vous pouvez définir le prototype uniquement sur un objet extensible. Pour plus d’informations, consultez [Object.preventextensions, fonction](../../javascript/reference/object-preventextensions-function-javascript.md).  
  
> [!NOTE]
>  Le `__proto__` nom de la propriété commence et se termine par deux traits de soulignement.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment définir le prototype pour un objet.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment ajouter des propriétés à un objet en les ajoutant au prototype.  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant ajoute des propriétés à l'objet `String` en définissant un nouveau prototype dessus.  
  
```JavaScript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Prototypes et héritage de prototype](../../javascript/advanced/prototypes-and-prototype-inheritance.md)