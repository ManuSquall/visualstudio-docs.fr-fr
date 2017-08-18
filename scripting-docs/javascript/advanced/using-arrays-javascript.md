---
title: Utilisation de tableaux (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript]
- arrays [JavaScript], objects
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 4c5218a8353a796128d8b672ecc781665c6bde20
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---
# <a name="using-arrays-javascript"></a>Utilisation de tableaux (JavaScript)
Les tableaux dans [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sont *partiellement alloués*. Autrement dit, si vous avez un tableau avec trois éléments numérotés 0, 1 et 2, vous pouvez créer l’élément 50 sans vous soucier des éléments 3 à 49. Si le tableau a une variable de longueur automatique (pour obtenir une explication de l’analyse automatique de la longueur d’un tableau, consultez [Objets intrinsèques](../../javascript/intrinsic-objects-javascript.md)), la variable de longueur est définie avec la valeur 51 et non 4. Vous pouvez créer des tableaux sans aucun écart dans la numérotation des éléments, mais vous n’êtes pas obligé de le faire.  
  
 Dans [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], les objets et les tableaux sont presque identiques. Les deux principales différences sont les suivantes : les objets qui ne sont pas des tableaux n’ont pas une propriété de longueur automatique, et les tableaux n’ont pas les propriétés et les méthodes d’un objet.  
  
## <a name="addressing-arrays"></a>Adressage des tableaux  
 Vous adressez les tableaux à l’aide de crochets ([]), comme indiqué dans l’exemple suivant. Les crochets entourent une valeur numérique ou une expression qui prend un nombre entier.  
  
```JavaScript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## <a name="objects-as-associative-arrays"></a>Objets comme tableaux associatifs  
 Vous utilisez généralement l’opérateur point (« . ») pour accéder aux propriétés d’un objet. Par exemple :  
  
```JavaScript  
myObject.aProperty  
```  
  
 Dans ce cas, le nom de la propriété est un identificateur. Vous pouvez également accéder aux propriétés d’un objet à l’aide de l’opérateur index ([]). Dans ce cas, vous traitez l’objet comme un *tableau associatif* dans lequel les valeurs de données sont associées à des chaînes. Par exemple :  
  
```JavaScript  
myObject["aProperty"] // Same as above.  
```  
  
 L’opérateur index sert généralement à accéder aux éléments d’un tableau. Quand il est utilisé avec des objets, l’index est un littéral de chaîne qui représente le nom de la propriété.  
  
 Notez les différences importantes entre les deux modes d’accès aux propriétés d’un objet.  
  
1.  Un nom de propriété traité comme un identificateur (syntaxe à point : « . ») ne peut pas être manipulé comme des données.  
  
2.  Un nom de propriété traité comme un index (syntaxe à crochets : « [] ») peut être manipulé comme des données.  
  
 Cette différence est utile quand vous ne connaissez pas les noms des propriétés avant l’exécution (par exemple, quand vous construisez des objets basés sur les entrées des utilisateurs). Pour extraire toutes les propriétés d’un tableau associatif, vous devez utiliser la boucle `for...in`.
