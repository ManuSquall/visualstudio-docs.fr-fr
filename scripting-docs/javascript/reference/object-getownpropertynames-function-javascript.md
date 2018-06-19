---
title: Object.getownpropertynames, fonction (JavaScript) | Documents Microsoft
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
helpviewer_keywords:
- getOwnPropertyNames method [JavaScript]
- Object.getOwnPropertyNames method [JavaScript]
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ca0036b9dedf7b4cee7b543469939e35dfe8d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639929"
---
# <a name="objectgetownpropertynames-function-javascript"></a>Object.getOwnPropertyNames, fonction (JavaScript)
Retourne les noms des propriétés d’un objet propres. Les propriétés propres d’un objet sont ceux qui sont définis directement sur cet objet et non hérités du prototype de l’objet. Les propriétés d’un objet incluent les fonctions et les champs (objets).  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
Object.getOwnPropertyNames(object)  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Définition|  
|---------------|----------------|  
|`object`|Obligatoire. Objet qui contient les propriétés propres.|  
  
## <a name="return-value"></a>Valeur de retour  
 Tableau qui contient les noms des propriétés propres de l’objet.  
  
## <a name="exceptions"></a>Exceptions  
 Si la valeur fournie pour le `object` argument n’est pas le nom d’un objet, un `TypeError` exception est levée.  
  
## <a name="remarks"></a>Remarques  
 Le `getOwnPropertyNames` méthode retourne les noms de propriétés énumérables et non énumérable et de méthodes. Pour retourner uniquement les noms des méthodes et propriétés énumérables, vous pouvez utiliser la [Object.Keys, fonction](../../javascript/reference/object-keys-function-javascript.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un objet qui possède trois propriétés et une méthode. Il utilise ensuite la `getOwnPropertyNames` méthode pour obtenir les propriétés propres (y compris la méthode) de l’objet.  
  
```JavaScript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant affiche les noms des propriétés qui commencent par la lettre ' dans un **spaghetti** objet construit avec le **pâtes** constructeur.  
  
```JavaScript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction Object.keys](../../javascript/reference/object-keys-function-javascript.md)