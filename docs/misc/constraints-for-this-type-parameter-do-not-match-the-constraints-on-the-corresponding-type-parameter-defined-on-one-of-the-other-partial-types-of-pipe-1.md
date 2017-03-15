---
title: "Les contraintes pour ce param&#232;tre de type ne correspondent pas aux contraintes du param&#232;tre de type correspondant d&#233;fini pour l’un des autres types partiels de &#39;|1&#39; | Microsoft Docs"
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
  - "vbc30932"
  - "bc30932"
helpviewer_keywords: 
  - "BC30932"
ms.assetid: a38ca4ad-6bbf-421e-a0d7-c5e0a9029160
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les contraintes pour ce param&#232;tre de type ne correspondent pas aux contraintes du param&#232;tre de type correspondant d&#233;fini pour l’un des autres types partiels de &#39;|1&#39;
Quand vous divisez la définition d’une classe ou d’une structure en plusieurs déclarations, le compilateur traite la classe ou la structure comme l’union de toutes ces déclarations partielles. Pour cette raison, vous ne pouvez pas définir des modificateurs ou des listes de paramètres de type contradictoires dans différentes déclarations partielles.  
  
 **ID d’erreur :** BC30932  
  
### Pour corriger cette erreur  
  
1.  Choisissez la liste de paramètres de type que vous voulez utiliser pour votre classe ou votre structure. Cette liste comprend les paramètres, l’ordre dans lequel ils se trouvent et les listes de contraintes qui leur sont associées.  
  
2.  Assurez\-vous que chaque définition partielle utilise la même liste de paramètres de type.  
  
## Voir aussi  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)