---
title: "Résolution des problèmes d’analyse de Code | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e552570eb48b9210b366ebbfe157fe656ab3fe0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-code-analysis-issues"></a>Résolution des problèmes liés à l'analyse du code
Cette rubrique contient des informations de dépannage pour les problèmes d’analyse de code Visual Studio suivants.  
  
-   [Modifications apportées à un Visual Studio 2010 règle jeu ne sont pas répercutées dans les Versions précédentes de Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a>Modifications apportées à un Visual Studio 2010 règle jeu ne sont pas répercutées dans les Versions précédentes de Visual Studio  
 Lorsque vous créez un ensemble de règles dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] qui contient un ensemble de règles enfant, une modification de l’ensemble de règles enfants ne soit pas appliquée dans les exécutions d’analyse du code sur les ordinateurs qui utilisent une version antérieure de Visual Studio. Pour résoudre ce problème, vous devez forcer une réécriture de l’ensemble de règles parent, qui est l’ensemble de règles qui contient l’ensemble de règles enfants.  
  
1.  Ouvrez la règle parente définie [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
2.  Apportez des modifications, telles que l’ajout ou la suppression d’une règle et enregistrez l’ensemble de règles.  
  
3.  Rouvrez l’ensemble de règles, d’annuler la modification, puis enregistrez l’ensemble de règles.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de la qualité de l’Application](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analyse de la qualité du Code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Utilisation d’ensembles de règles pour regrouper des règles d’analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)