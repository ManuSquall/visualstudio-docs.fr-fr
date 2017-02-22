---
title: "Balises Symbols et Symbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symboles (DIA SDK)"
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Balises Symbols et Symbol
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les informations de débogage concernant un programme compilé sont stockées dans le fichier de base de données du programme \(.pdb\) comme symboles qui sont accessibles à l'aide de les API d'Accès Kit de \(DIA\) développement logiciel d'interface de débogage.  Tous les symboles auront [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md) et une propriété de [IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) .  La propriété d' `symTag` indique le type de symbole défini par l'énumération de [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md) .  la propriété d' `symIndexId` est une valeur d' `DWORD` qui contient l'identificateur unique pour chaque instance d'un symbole.  
  
 Les symboles ont également des propriétés qui peuvent spécifier des informations supplémentaires sur le symbole ainsi que des références à d'autres symboles, le plus souvent [IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) ou [IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md).  Lorsque vous interrogez une propriété qui contient une référence, la référence est retournée comme un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) .  De telles propriétés sont toujours couplées avec une autre propriété par le même nom mais suffixées avec « identificateur », par exemple, un [IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) et un [IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md).  Les tables dans le plan de [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md), de [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), et de [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) les propriétés pour chacun des différents genres de symboles.  Ces propriétés peuvent avoir des informations importantes sur les scénarios ou des références à d'autres symboles.  Étant donné que les propriétés d' `*Id` sont les identificateurs ordinaux simplement numériques de leurs propriétés connexes, elles sont omises d'autres de discussions.  Ils sont référencés uniquement lorsque cela est nécessaire pour pouvoir clarification de paramètre.  
  
 Lors d'une tentative d'accès à la propriété, si aucune erreur ne se produit et la propriété de symbole a été assignée à une valeur, la méthode de « get » de la propriété retourne `S_OK`.  Une valeur de retour d' `S_FALSE` indique que la propriété n'est pas valide pour le symbole actuel.  
  
## Dans cette section  
 [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)  
 décrit les différents genres d'emplacements qu'un symbole peut avoir.  
  
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Décrit les types de symboles qui forment des hiérarchies lexicales telles que les fichiers, les modules, les fonctions et.  
  
 [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Décrit les types de symboles qui correspondent à des éléments de langage tels que les classes, les tableaux, les types de retour de fonction.  
  
## Voir aussi  
 [Kit de développement logiciel de Debug Interface Access](../../debugger/debug-interface-access/debug-interface-access-sdk.md)