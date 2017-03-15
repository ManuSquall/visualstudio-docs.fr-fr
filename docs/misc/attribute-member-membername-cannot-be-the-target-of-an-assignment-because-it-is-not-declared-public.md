---
title: "Le membre d’attribut &#39;&lt;nom_membre&gt;&#39; ne peut pas &#234;tre la cible d’une assignation, car il n’est pas d&#233;clar&#233; &#39;Public&#39; | Microsoft Docs"
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
  - "vbc31511"
  - "bc31511"
helpviewer_keywords: 
  - "BC31511"
ms.assetid: f8c958f6-58a4-4aff-b8c3-f2e9481e8132
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le membre d’attribut &#39;&lt;nom_membre&gt;&#39; ne peut pas &#234;tre la cible d’une assignation, car il n’est pas d&#233;clar&#233; &#39;Public&#39;
Vous avez essayé d’assigner une valeur à un membre privé d’un attribut.  
  
 **ID d’erreur :** BC31511  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’assignation.  
  
2.  Si vous utilisez des attributs personnalisés que vous avez développés, affectez `Public` comme modificateur d’accès du membre d’attribut.  
  
## Voir aussi  
 [NOT IN BUILD : Attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)