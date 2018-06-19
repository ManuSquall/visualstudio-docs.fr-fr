---
title: Cette instruction (JavaScript) | Documents Microsoft
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
- this_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- this statement
- constructors, referring to current object
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4afed1bd978d1985c151efa77873c93e699f0b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640319"
---
# <a name="this-statement-javascript"></a>this, instruction (JavaScript)
Fait référence à l'objet en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
this.property  
```  
  
## <a name="remarks"></a>Remarques  
 L'argument `property` requis est l'une des propriétés de l'objet actif  
  
 Le mot clé `this` peut être employé dans des constructeurs d'objet pour faire référence à l'objet actif.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, **cela** fait référence au nouvel objet Car et assigne des valeurs à trois propriétés :  
  
```JavaScript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 Le **cela** mot clé fait généralement référence à la **fenêtre** si utilisé en dehors de la portée de tout autre objet de l’objet. Toutefois, dans les gestionnaires d'événements `this` fait référence à l'élément DOM qui a déclenché l'événement.  
  
 Dans le code suivant (pour Internet Explorer 9 et versions ultérieures), le gestionnaire d'événements imprime la version chaîne d'un bouton qui a un ID de « cliqueur ».  
  
```JavaScript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Utilisation de la méthode Bind](../../javascript/advanced/using-the-bind-method-javascript.md)