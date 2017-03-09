---
title: "unchecked_adjacent_difference | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.unchecked_adjacent_difference"
  - "std::unchecked_adjacent_difference"
  - "unchecked_adjacent_difference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unchecked_adjacent_difference (fonction)"
ms.assetid: 3a6b0b49-a84b-40b1-bcd5-3bf76c6ef7d7
caps.latest.revision: 14
caps.handback.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
---
# unchecked_adjacent_difference
Identique à [adjacent\_difference](../Topic/adjacent_difference.md), mais permet l’utilisation d’un itérateur non vérifié comme itérateur de sortie lorsque \_SECURE\_SCL \= 1 est défini.`unchecked_adjacent_difference` est défini dans le `stdext` espace de noms.  
  
> [!NOTE]
>  Cet algorithme est une extension Microsoft de la bibliothèque C\+\+ standard. Le code implémenté à l'aide de cet algorithme n'est pas portable.  
  
## Syntaxe  
  
```  
template<class InputIterator, class OutIterator>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result   
   );  
  
template<class InputIterator, class OutputIterator, class BinaryOperation>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result,   
      BinaryOperation _Binary_op  
   );  
```  
  
#### Paramètres  
 `_First`  
 Itérateur d'entrée qui traite le premier élément d'une plage d'entrée dont les éléments doivent être différenciés de leurs prédécesseurs respectifs, ou bien, dont la paire de valeurs doit être utilisée dans le cadre d'une opération par une opération binaire spécifiée.  
  
 `_Last`  
 Itérateur d'entrée qui traite le dernier élément d'une plage d'entrée dont les éléments doivent être différenciés de leurs prédécesseurs respectifs, ou bien, dont la paire de valeurs doit être utilisée dans le cadre d'une opération par une opération binaire spécifiée.  
  
 `_Result`  
 Itérateur de sortie qui traite le premier élément d'une plage de destination dans laquelle les différences ou les résultats de l'opération spécifiée doivent être enregistrés.  
  
 `_Binary_op`  
 Opération binaire qui doit être appliquée dans l'opération généralisée par le remplacement de l'opération de soustraction de la procédure de différenciation.  
  
## Valeur de retour  
 Itérateur de sortie traite la fin de la plage de destination : `_Result` \+ \(`_Last` \- `_First`\).  
  
## Notes  
 Consultez [adjacent\_difference](../Topic/adjacent_difference.md) pour obtenir un exemple de code.  
  
 Pour plus d’informations sur les itérateurs vérifiés, consultez [Itérateurs vérifiés](/visual-cpp/standard-library/checked-iterators).  
  
## Configuration requise  
 **En\-tête :** \<numeric\>  
  
 **Espace de noms :** stdext  
  
## Voir aussi  
 [Bibliothèque STL \(Standard Template Library\)](../misc/standard-template-library.md)