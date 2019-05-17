---
title: Création et utilisation de stratégies d’archivage de l’analyse du Code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3a8015eb672e87431a1d225221ff2321c41e041a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697052"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Création et utilisation de stratégies d’archivage de l’analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous utilisez Team Foundation Version Control (TFVC), vous pouvez créer une stratégie d’archivage de l’analyse du code pour le .NET Framework et les projets de code natifs (C/C++) dans un projet d’équipe. Vous pouvez utiliser la stratégie d’archivage de l’analyse du code pour contrôler et améliorer la qualité du code est archivé dans la base de code.  
  
 La stratégie est passée lorsque la version locale est à jour et d’analyse du code a été exécutée sur les fichiers les plus récents de la source. Au minimum, les règles d’analyse de code qui sont activées dans le projet de code doivent contenir les mêmes règles que celles qui sont définies dans la stratégie projet d’équipe archivage. Les règles qui ont été spécifiés comme des erreurs dans les paramètres de projet d’équipe doivent également être spécifiés comme des erreurs dans le projet de code  
  
> [!IMPORTANT]
> Stratégies d’archivage de l’analyse du code ne peut pas être appliqués aux projets de site web. Elles peuvent être appliquées aux projets d’application web.  
  
 Vous créez des code de stratégies d’archivage de l’analyse à l’aide des paramètres de projet d’équipe [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Stratégies d’archivage sont spécifiées et appliquées pour un projet d’équipe, mais les exécutions d’analyse du code sont configurées et exécutées pour les projets de code individuels sur les ordinateurs de développement local. Cette section décrit comment spécifier le code analysis stratégies d’archivage pour un projet d’équipe et comment implémenter des stratégies d’analyse du code personnalisé pour le code managé.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour Créer ou mettre à jour des stratégies d’archivage de l’analyse du Code Standard](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Explique les étapes que vous utilisez pour définir et modifier une stratégie d’analyse de code pour un projet d’équipe.  
  
 [Implémentation de stratégies d’archivage personnalisées pour le code managé](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Explique les étapes que vous utilisez pour créer une règle personnalisée définie pour la stratégie d’archivage d’un projet d’équipe et de synchroniser les projets de code du projet d’équipe avec la stratégie d’archivage.  
  
 [Compatibilité des versions des stratégies d’archivage de l’analyse du code](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Explique les problèmes de compatibilité d’archivage d’analyse code entre les versions de [!INCLUDE[vstsLong](../includes/vstslong-md.md)].  
  
 [Guide pratique pour Personnaliser le dictionnaire d’analyse du Code](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Explique comment ajouter des mots et des jetons au dictionnaire référencé dans les règles d’affectation de noms d’analyse du code.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Définir et appliquer des critères de qualité](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [Amélioration de la qualité du code avec les stratégies d’archivage de projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
