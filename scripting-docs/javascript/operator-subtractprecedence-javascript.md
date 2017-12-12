---
title: "Precedence, opérateur (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- operator precedence
- order of precedence
ms.assetid: cf3c510a-2214-4b47-b8fe-3521298efaab
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82503a312a4a4996e3bd38f596eef3104af3f11b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="operator-precedence-javascript"></a>Precedence, opérateur (JavaScript)
La priorité des opérateurs décrit l'ordre dans lequel les opérations sont exécutées lors de l'évaluation d'une expression. Les opérations ayant une priorité élevée sont effectuées avant les autres. Par exemple, la multiplication est effectuée avant l'addition.  
  
## <a name="includejavascriptjavascriptincludesjavascript-mdmd-operators"></a>[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] Opérateurs  
 Le tableau ci-dessous répertorie les opérateurs [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] par ordre de priorité décroissant. Les opérateurs de même priorité sont évalués de gauche à droite.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|. [ ] ( )|Accès aux champs, indexage de tableau, appels de fonction et regroupement d'expressions|  
|++ -- - ~ ! delete new typeof void|Opérateurs unaires, type de données retour, création d'objet, valeurs indéfinies|  
|* / %|Multiplication, division, division modulo|  
|+ - +|Addition, soustraction, concaténation de chaînes|  
|<\< >> >>>|Décalage de bits|  
|< \<= > >= instanceof|Inférieur à, inférieur ou égal à, supérieur à, supérieur ou égal à, instance de|  
|== != === !==|Égalité, inégalité, identité, non-identité|  
|&|Opération de bits AND|  
|^|Opération de bits XOR|  
|&#124;|Opération de bits OR|  
|&&|AND logique|  
|&#124;&#124;|OR logique|  
|?:|Conditionnel|  
|= *OP*=|Assignation, assignation avec opération (comme += et &=)|  
|,|Évaluation multiple|  
  
 Les parenthèses sont utilisées pour modifier l'ordre d'évaluation déterminé par la priorité des opérateurs. Une expression entre parenthèses fait l'objet d'une évaluation complète avant que sa valeur ne soit utilisée dans le reste de l'expression.  
  
 Exemple :  
  
```JavaScript  
var result = 78 * 96 + 3;  
document.write(result);  
document.write("<br/>");  
  
result = 78 * (9 + 3);  
document.write(result);  
  
// Output:  
// 7491  
// 936  
```  
  
 La première expression contient trois opérateurs : =, *, et +. Conformément aux règles de priorité, ils sont évalués dans l’ordre suivant : \*, +, = (78 \* 96 = 7488, 7488 + 3 = 7491).  
  
 Dans la deuxième expression, l’opérateur ( ) est évalué en premier, afin que l’expression d’addition soit évaluée avant la multiplication (9 + 3 = 12, 12 *+ 78 = 936).  
  
 L'exemple suivant illustre une instruction qui inclut divers opérateurs et se résout en `true`.  
  
```JavaScript  
var num = 10;  
  
if(5 == num / 2 && (2 + 2 * num).toString() === "22") {  
    document.write(true);  
}  
    // Output:  
    // true  
```  
  
 Les opérateurs sont évalués dans l’ordre suivant : () pour le regroupement, *, + (au sein du groupe), « . » pour la fonction, ( ) pour la fonction, /, ==, ===, et &&.