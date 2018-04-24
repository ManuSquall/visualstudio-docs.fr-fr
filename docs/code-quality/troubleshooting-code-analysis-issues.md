---
title: Résolution des problèmes liés à l'analyse du code
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9029c7be21fe02b9d6b1c4436658df74eb3c37f9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
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
 [Analyse de la qualité de l’Application](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md) [analyse de la qualité du Code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) [à l’aide de la règle définit aux règles d’analyse de Code de groupe](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)