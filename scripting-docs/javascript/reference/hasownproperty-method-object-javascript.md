---
title: "hasOwnProperty, méthode (Object) (JavaScript) | Documents Microsoft"
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
- hasOwnProperty
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hasOwnProperty method
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 397b68fc87bf730886c928e099037ff0183a7f63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="hasownproperty-method-object-javascript"></a>hasOwnProperty, méthode (Object) (JavaScript)
Détermine si un objet possède une propriété portant le nom spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. Instance d’un objet.  
  
 `proName`  
 Obligatoire. Valeur de chaîne d’un nom de propriété.  
  
## <a name="remarks"></a>Remarques  
 Le `hasOwnProperty` méthode retourne `true` si `object` a une propriété portant le nom spécifié, `false` si elle n’est pas le cas. Cette méthode ne vérifie pas les propriétés dans la chaîne de prototype de l’objet ; la propriété doit être un membre de l’objet lui-même.  
  
 Cette propriété n’est pas pris en charge sur les objets de l’ordinateur hôte pour Internet Explorer 8 et en dessous.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, tous les `String` objets partagent une méthode de fractionnement commune. Le code suivant affiche **false** et **true**.  
  
```JavaScript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateur In](../../javascript/reference/in-operator-decrementjavascript.md)