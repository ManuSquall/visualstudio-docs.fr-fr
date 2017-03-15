---
title: "Le nom du param&#232;tre de type &#39;&lt;nom_param&#232;tre_type1&gt;&#39; ne correspond pas au nom &#39;&lt;nom_param&#232;tre_type2&gt;&#39; du param&#232;tre de type correspondant d&#233;fini pour l’un des autres types partiels de &#39;&lt;nom_type_partiel&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30931"
  - "bc30931"
helpviewer_keywords: 
  - "BC30931"
ms.assetid: 01b053c3-d1b5-4e69-b908-3d5cfc73913b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le nom du param&#232;tre de type &#39;&lt;nom_param&#232;tre_type1&gt;&#39; ne correspond pas au nom &#39;&lt;nom_param&#232;tre_type2&gt;&#39; du param&#232;tre de type correspondant d&#233;fini pour l’un des autres types partiels de &#39;&lt;nom_type_partiel&gt;&#39;
Une classe ou une structure générique est définie dans plusieurs déclarations partielles avec des spécifications de paramètre de type incompatibles.  
  
 Quand vous divisez la définition d’une classe ou d’une structure en plusieurs déclarations partielles, le compilateur traite le type comme l’union de toutes ses déclarations partielles. Cela s’applique non seulement aux membres, mais également à l’implémentation, à l’héritage et au niveau d’accès.  
  
 Vous ne pouvez pas spécifier plusieurs noms pour un paramètre de type dans la définition d’une classe ou d’une structure générique.  
  
 **ID d’erreur :** BC30931  
  
### Pour corriger cette erreur  
  
-   Définissez le nom souhaité pour le paramètre de type et utilisez ce même nom dans chaque déclaration partielle.  
  
## Voir aussi  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [NOT IN BUILD : Classes : modèles d’objets](http://msdn.microsoft.com/fr-fr/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Structures](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)