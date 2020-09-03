---
title: Résolution des problèmes liés à l’analyse du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6fd2735b7e601afb5a80dd027a8ae107cab58e4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672424"
---
# <a name="troubleshooting-code-analysis-issues"></a>Résolution des problèmes liés à l'analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique contient des informations de résolution des problèmes suivants liés à l’analyse du code Visual Studio.

- [Les modifications apportées à un ensemble de règles Visual Studio 2010 ne sont pas reflétées dans les versions précédentes de Visual Studio](#ChildRuleSetChangesInPreviousVersions)

## <a name="changes-in-a-visual-studio-2010-rule-set-are-not-reflected-in-previous-visual-studio-versions"></a><a name="ChildRuleSetChangesInPreviousVersions"></a> Des modifications apportées à un ensemble de règles de Visual Studio 2010 ne sont pas répercutées dans les versions antérieures de Visual Studio
 Quand vous créez un ensemble de règles dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] qui contient un ensemble de règles enfant, une modification de cet ensemble de règles peut ne pas être appliquée dans les exécutions de l’analyse du code sur des ordinateurs qui utilisent une version antérieure de Visual Studio. Pour résoudre ce problème, vous devez forcer une réécriture de l’ensemble de règles parent, qui est l’ensemble de règles contenant l’ensemble de règles enfant.

1. Ouvrez l’ensemble de règles parent dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].

2. Faites une modification, comme ajouter ou supprimer une règle, puis enregistrez l’ensemble de règles.

3. Rouvrez l’ensemble de règles, annulez la modification, puis réenregistrez l’ensemble de règles.

## <a name="see-also"></a>Voir aussi
 [Analyse](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md) de la qualité des applications analyse de la [qualité du code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) à [l’aide d’ensembles de règles pour regrouper des règles](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
