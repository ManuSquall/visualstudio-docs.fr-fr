---
title: Résolution des problèmes liés à l’analyse du code | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d50bbe4a5969d0614370e0aa0e1a15455b6a458a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-code-analysis-issues"></a>Résolution des problèmes liés à l'analyse du code
Cette rubrique contient des informations de résolution des problèmes suivants liés à l’analyse du code Visual Studio.  
  
-   [Des modifications apportées à un ensemble de règles de Visual Studio 2010 ne sont pas répercutées dans les versions antérieures de Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Des modifications apportées à un ensemble de règles de Visual Studio 2010 ne sont pas répercutées dans les versions antérieures de Visual Studio  
 Quand vous créez un ensemble de règles dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] qui contient un ensemble de règles enfant, une modification de cet ensemble de règles peut ne pas être appliquée dans les exécutions de l’analyse du code sur des ordinateurs qui utilisent une version antérieure de Visual Studio. Pour résoudre ce problème, vous devez forcer une réécriture de l’ensemble de règles parent, qui est l’ensemble de règles contenant l’ensemble de règles enfant.  
  
1.  Ouvrez l’ensemble de règles parent dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
2.  Faites une modification, comme ajouter ou supprimer une règle, puis enregistrez l’ensemble de règles.  
  
3.  Rouvrez l’ensemble de règles, annulez la modification, puis réenregistrez l’ensemble de règles.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de la qualité des applications](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Utilisation d’ensembles de règles pour regrouper des règles d’analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)