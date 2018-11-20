---
title: Résolution des problèmes liés à l’analyse du code | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a044b0682b5ac70fc38df3080ef435c5ab6aad3b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768214"
---
# <a name="troubleshooting-code-analysis-issues"></a>Résolution des problèmes liés à l'analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique contient des informations de résolution des problèmes suivants liés à l’analyse du code Visual Studio.  
  
-   [Des modifications apportées à un ensemble de règles de Visual Studio 2010 ne sont pas répercutées dans les versions antérieures de Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Des modifications apportées à un ensemble de règles de Visual Studio 2010 ne sont pas répercutées dans les versions antérieures de Visual Studio  
 Quand vous créez un ensemble de règles dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] qui contient un ensemble de règles enfant, une modification de cet ensemble de règles peut ne pas être appliquée dans les exécutions de l’analyse du code sur des ordinateurs qui utilisent une version antérieure de Visual Studio. Pour résoudre ce problème, vous devez forcer une réécriture de l’ensemble de règles parent, qui est l’ensemble de règles contenant l’ensemble de règles enfant.  
  
1.  Ouvrez l’ensemble de règles parent dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
2.  Faites une modification, comme ajouter ou supprimer une règle, puis enregistrez l’ensemble de règles.  
  
3.  Rouvrez l’ensemble de règles, annulez la modification, puis réenregistrez l’ensemble de règles.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de la qualité des applications](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Utilisation d’ensembles de règles pour regrouper des règles d’analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)



