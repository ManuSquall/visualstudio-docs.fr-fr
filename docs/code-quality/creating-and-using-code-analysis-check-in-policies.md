---
title: "Création et utilisation de stratégies d’archivage de l’analyse du Code | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b16b7e9f4dba55babfc7ad2ad90affe0ca93c508
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Création et utilisation de stratégies d’archivage de l’analyse du code
Lorsque vous utilisez Team Foundation Version Control (TFVC), vous pouvez créer une stratégie d’archivage de l’analyse du code pour le .NET Framework et les projets de code natifs (C/C++) dans un projet d’équipe. Vous pouvez utiliser la stratégie d’archivage de l’analyse du code pour contrôler et améliorer la qualité du code archivé dans la base de code.  
  
 La stratégie a réussi lors de la version locale est à jour et d’analyse du code a été exécutée sur les fichiers les plus récents de la source. Au minimum, les règles d’analyse de code qui sont activées dans le projet de code doivent contenir les mêmes règles que celles qui sont définies dans la stratégie projet d’équipe archivage. Les règles qui ont été spécifiés comme des erreurs dans les paramètres de projet d’équipe doivent également être spécifiés en tant qu’erreurs dans le projet de code  
  
> [!IMPORTANT]
>  Stratégies d’archivage de l’analyse du code ne peut pas être appliqués aux projets de site web. Ils peuvent être appliqués aux projets d’application web.  
  
 Créer code de stratégies d’archivage de l’analyse à l’aide des paramètres de projet d’équipe [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]. Stratégies d’archivage sont spécifiées et appliquées pour un projet d’équipe, mais les exécutions d’analyse du code sont configurées et exécutées pour les projets de code individuels sur les ordinateurs de développement local. Cette section décrit comment spécifier le code analysis stratégies d’archivage pour un projet d’équipe et comment implémenter des stratégies d’analyse du code personnalisées pour le code managé.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour créer ou mettre à jour des stratégies d’archivage d’analyse du code standard](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Explique les étapes que vous utilisez pour définir et modifier une stratégie d’analyse de code pour un projet d’équipe.  
  
 [Implémentation de stratégies d’archivage personnalisées pour le Code managé](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Explique les étapes que vous utilisez pour créer une règle personnalisée définie pour la stratégie d’archivage d’un projet d’équipe et de synchroniser les projets de code du projet d’équipe avec la stratégie d’archivage.  
  
 [Compatibilité des versions des stratégies d’archivage de l’analyse du code](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Explique les problèmes de compatibilité d’archivage d’analyse code entre les versions de [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)].  
  
 [Guide pratique pour personnaliser le dictionnaire d’analyse du code](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Explique comment ajouter des mots et des jetons au dictionnaire référencé dans les règles d’affectation des noms d’analyse du code.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Définir et appliquer des critères de qualité](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [Amélioration de la qualité du code avec les stratégies d’archivage de projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)