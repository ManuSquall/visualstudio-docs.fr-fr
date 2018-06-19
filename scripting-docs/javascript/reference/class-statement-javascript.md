---
title: Class, instruction (JavaScript) | Documents Microsoft
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
ms.assetid: bf45ebad-4678-4062-88df-55d32b603c69
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e828ae86c3f8f585179e3b097d98b3449c3f3b45
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634229"
---
# <a name="class-statement-javascript"></a>class, instruction (JavaScript)
Déclare une nouvelle classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class classname () [extends object] {    [constructor([arg1 [,... [,argN]]]) {        statements    }]    [[static] method([arg1 [,... [,argN]]]) {        statements    }]}  
```  
  
#### <a name="parameters"></a>Paramètres  
 `classname`  
 Obligatoire. Nom de la classe.  
  
 `object`  
 Facultatif. Objet ou classe à partir duquel ou de laquelle la nouvelle classe hérite des propriétés et méthodes.  
  
 `constructor`  
 Facultatif. Fonction de constructeur qui initialise la nouvelle instance de la classe.  
  
 `arg1...argN`  
 Facultatif. Liste facultative d’arguments séparés par des virgules que comprend la fonction.  
  
 `statements`  
 Facultatif. Une ou plusieurs instructions [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 `static`  
 Facultatif. Spécifie une méthode statique.  
  
 `method`  
 Facultatif. Une ou plusieurs méthodes statiques ou d'instance [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] qui peuvent être appelées sur une instance de classe.  
  
## <a name="remarks"></a>Remarques  
 Une classe vous permet de créer des objets à l'aide de l'héritage de prototype, des constructeurs, des méthodes d'instance et des méthodes statiques. Vous pouvez utiliser l'objet `super` dans un constructeur de classe ou une méthode de classe pour appeler le même constructeur ou la même méthode dans la classe ou l'objet parent. Vous pouvez également utiliser l'instruction `extends` après le nom de classe pour spécifier l'objet ou la classe à partir duquel ou de laquelle la nouvelle classe hérite des méthodes.  
  
## <a name="example"></a>Exemple  
  
```JavaScript  
class Spelunking extends EXPERIENCE.Outdoor {  
  constructor(name, location) {  
    super(name, location);  
  
    this.minSkill = Spelunking.defaultSkill();  
    //...  
  }  
  update(minSkill) {  
    //...  
    super.update(minSkill);  
  }  
  static defaultSkill() {  
    return new EXPERIENCE.Level3();  
  }  
}  
```  
  
## <a name="example"></a>Exemple  
 Vous pouvez également créer des noms de propriété calculée pour les classes. L'exemple de code suivant crée un nom de propriété calculée à l'aide de la syntaxe `set`.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    set [propName](v) {  
        this.value = v;  
    }  
};  
  
var s = new Spelunking();  
console.log(s.value);  
s.prop_42 = 42;  
console.log(s.value);  
  
// Output:  
// undefined  
// 42  
  
```  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant crée un nom de propriété pour une classe dynamiquement à l'aide de la syntaxe `get`.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    get [propName]() {  
        return 777;  
    }  
}  
  
var s = new Spelunking();  
console.log(s.prop_42);  
  
// Output:  
// 777  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12exp](../../javascript/reference/includes/jsv12exp-md.md)]