---
title: "R&#233;solution des probl&#232;mes li&#233;s &#224; l&#39;analyse du code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 5
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 5
---
# R&#233;solution des probl&#232;mes li&#233;s &#224; l&#39;analyse du code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique contient les informations de résolution pour les problèmes suivants d'analyse du code Visual Studio.  
  
-   [Les modifications apportées à un ensemble de règles Visual Studio 2010 ne sont pas répercutées dans les versions antérieures de Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Les modifications apportées à un ensemble de règles Visual Studio 2010 ne sont pas répercutées dans les versions antérieures de Visual Studio  
 Lorsque vous créez un ensemble de règles dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] qui contient un ensemble de règles enfant, une modification de l'ensemble de règles enfant peut ne pas être appliquée dans les exécutions d'analyse du code sur les ordinateurs qui utilisent une version antérieure de Visual Studio.  Pour résoudre ce problème, vous devez forcer une réécriture de l'ensemble de règles parent, qui est l'ensemble de règles contenant l'ensemble de règles enfant.  
  
1.  Ouvrez l'ensemble de règles parent défini dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
2.  Apportez une modification, telle que l'ajout ou la suppression d'une règle, puis enregistrez l'ensemble de règles.  
  
3.  Rouvrez l'ensemble de règles, inversez la modification, puis réenregistrez l'ensemble de règles.  
  
## Voir aussi  
 [Analyse de la qualité des applications](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Utilisation d'ensembles de règles pour regrouper des règles d'analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)