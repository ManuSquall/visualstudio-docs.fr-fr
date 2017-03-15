---
title: "Le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; ne peut avoir qu’une seule contrainte qui est une classe. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32047"
  - "vbc32047"
helpviewer_keywords: 
  - "BC32047"
ms.assetid: ac7ab76b-5300-4c79-b519-5a1287ed5fa9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; ne peut avoir qu’une seule contrainte qui est une classe.
Une liste de contraintes contient plusieurs classes.  
  
 Une liste de contraintes appliquée à un paramètre de type peut accepter n’importe quel nombre d’interfaces, mais une classe au maximum. Un argument de type fourni pour ce paramètre de type doit hériter de cette classe, et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne prend pas en charge l’héritage multiple.  
  
 **ID d’erreur :** BC32047  
  
### Pour corriger cette erreur  
  
-   Choisissez une seule et même classe et incluez\-la dans la liste des contraintes.  
  
-   Vous pourrez éventuellement définir des paramètres de type supplémentaires pour intégrer la ou les classes que vous n’avez pas pu inclure dans cette liste de contraintes.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)