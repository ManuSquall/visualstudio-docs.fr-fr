---
title: "Définir l’objet (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Set
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5134ec09c9a8642499212af9dd5fd44de0068adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="set-object-javascript"></a>Set, objet (JavaScript)
Collection de valeurs uniques de n’importe quel type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
setObj = new Set()     
```  
  
## <a name="remarks"></a>Remarques  
 Si vous essayez d’ajouter une valeur non unique à un `Set`, la nouvelle valeur ne sera pas être ajoutée à la collection.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Set`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[constructeur](../../javascript/reference/constructor-property-set.md)|Spécifie la fonction qui crée un ensemble.|  
|[prototype](../../javascript/reference/prototype-property-set.md)|Retourne une référence au prototype pour un ensemble.|  
|[size](../../javascript/reference/size-property-set-javascript.md)|Retourne le nombre d’éléments dans un jeu.|  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Set`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[add](../../javascript/reference/add-method-set-javascript.md)|Ajoute un élément à un ensemble.|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|Supprime tous les éléments d’un ensemble.|  
|[supprimer](../../javascript/reference/delete-method-set-javascript.md)|Supprime un élément spécifié d'un ensemble.|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|Exécute l’action spécifiée pour chaque élément dans un jeu.|  
|[a](../../javascript/reference/has-method-set-javascript.md)|Retourne `true` si l'ensemble contient l'élément spécifié.|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|Retourne une représentation sous forme de chaîne d’un jeu.|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|Retourne la valeur primitive de l'objet spécifié.|  
  
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