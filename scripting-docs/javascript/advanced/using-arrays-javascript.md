---
title: "Utilisation de tableaux (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "tableaux (JavaScript)"
  - "tableaux (JavaScript), objets"
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Utilisation de tableaux (JavaScript)
Les tableaux dans [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sont *creux*.  Autrement dit, si vous avez un tableau de trois éléments qui sont numérotés 0, 1 et 2, vous pouvez créer l'élément 50 sans vous préoccuper des éléments 3 à 49.  Si le tableau a une variable de longueur automatique \(consultez [Objets intrinsèques](../../javascript/intrinsic-objects-javascript.md) pour obtenir une explication sur le contrôle automatique de la longueur des tableaux\), la variable de longueur a la valeur 51, plutôt que 4.  Vous pouvez créer des tableaux dans lesquels il n'y a pas d'espaces vides dans la numérotation des éléments, mais vous n'êtes pas tenu de le faire.  
  
 Dans [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], les objets et les tableaux sont presque identiques entre eux.  Il existe toutefois deux différences principales : les objets non\-tableaux ne disposent pas d'une propriété de longueur automatique et les tableaux ne possèdent ni les propriétés, ni les méthodes d'un objet.  
  
## Adressage des tableaux  
 Vous adressez des tableaux en utilisant des crochets \(\[\]\), comme indiqué dans l'exemple suivant.  Les crochets encadrent une valeur numérique ou une expression qui correspond à un nombre entier.  
  
```javascript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## Objets sous forme de tableaux associatifs  
 Vous utilisez généralement l'opérateur point « . » pour accéder aux propriétés d'un objet.  Par exemple :  
  
```javascript  
myObject.aProperty  
```  
  
 Dans ce cas, le nom de la propriété est un identificateur.  Vous pouvez également accéder aux propriétés d'un objet en utilisant l'opérateur index \(\[\]\).  Dans ce cas, vous traitez l'objet comme un *tableau associatif* dans lequel les valeurs de données sont associées à des chaînes.  Par exemple :  
  
```javascript  
myObject["aProperty"] // Same as above.  
```  
  
 L'opérateur index sert plus généralement à accéder aux éléments de tableaux.  Lorsqu'il est utilisé avec des objets, l'index est un littéral de chaîne qui représente le nom de la propriété.  
  
 Notez les différences essentielles entre les deux modes d'accès aux propriétés d'un objet.  
  
1.  Un nom de propriété traité comme un identificateur \(la syntaxe de point \(.\)\) ne peut pas être manipulé comme des données.  
  
2.  Un nom de propriété traité comme un index \(syntaxe d'accolades \(\[\]\)\) peut être manipulé comme des données.  
  
 Cette différence prend toute sa signification lorsque vous ignorez, jusqu'au moment de l'exécution, les noms des propriétés \(par exemple, lorsque vous construisez des objets fondés sur des entrées utilisateur\).  Pour extraire toutes les propriétés d'un tableau associatif, vous devez utiliser une boucle `for…in`.