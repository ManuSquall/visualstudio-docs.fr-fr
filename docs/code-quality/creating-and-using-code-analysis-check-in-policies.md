---
title: "Cr&#233;ation et utilisation de strat&#233;gies d&#39;archivage de l&#39;analyse du code | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analyse du code, stratégies d'archivage"
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 39
caps.handback.revision: 39
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cr&#233;ation et utilisation de strat&#233;gies d&#39;archivage de l&#39;analyse du code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous utilisez Team Foundation Version Control \(TFVC\), vous pouvez créer une stratégie d'archivage d'analyse du code pour les projets de code .NET Framework et natif \(C\/C\+\+\) dans un projet d'équipe.  Vous pouvez utiliser cette stratégie pour contrôler et améliorer la qualité du code qui est archivé dans la base de code.  
  
 La stratégie est passée lorsque la version locale est à jour et que l'analyse du code a été exécutée sur les fichiers sources les plus récents.  Au minimum, les règles d'analyse du code permises dans le projet de code doivent contenir les mêmes règles que celles définies dans la stratégie d'archivage du projet d'équipe.  Les règles spécifiées comme erreurs dans les Paramètres du projet d'équipe doivent également être spécifiées comme erreurs dans le projet de code.  
  
> [!IMPORTANT]
>  Les stratégies d'archivage d'analyse du code ne peuvent pas être appliquées aux projets de site Web.  Elles peuvent être appliquées aux projets d'application Web.  
  
 Vous créez des stratégies d'archivage d'analyse du code à l'aide des Paramètres du projet d'équipe du [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)].  Les stratégies d'archivage sont spécifiées et appliquées pour un projet d'équipe, mais les analyses du code sont configurées et exécutées pour les projets de code individuels sur les ordinateurs de développement locaux.  Cette section décrit comment spécifier des stratégies d'archivage d'analyse du code pour un projet d'équipe et implémenter des stratégies d'analyse du code personnalisées pour le code managé.  
  
## Dans cette section  
 [Comment : créer ou mettre à jour des stratégies d'archivage d'analyse du code standard](../Topic/How%20to:%20Create%20or%20Update%20Standard%20Code%20Analysis%20Check-in%20Policies.md)  
 Explique les étapes à utiliser pour définir et modifier une stratégie d'analyse du code pour un projet d'équipe.  
  
 [Implémentation de stratégies d'archivage personnalisées pour le code managé](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Explique les étapes à utiliser pour créer un ensemble de règles personnalisées pour la stratégie d'archivage d'un projet d'équipe et synchroniser les projets de code du projet d'équipe avec la stratégie d'archivage.  
  
 [Compatibilité des versions des stratégies d'archivage de l'analyse du code](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Explique les problèmes de compatibilité d'archivage de l'analyse du code entre les différentes versions de [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)].  
  
 [Comment : personnaliser le dictionnaire d’analyse du code](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)  
 Explique comment ajouter des mots et des jetons au dictionnaire référencé dans les règles d'affectation des noms pour l'analyse du code.  
  
## Rubriques connexes  
 [Set and Enforce Quality Gates](../Topic/Set%20and%20Enforce%20Quality%20Gates.md)  
  
 [Amélioration de la qualité du code avec des stratégies d’archivage de projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)