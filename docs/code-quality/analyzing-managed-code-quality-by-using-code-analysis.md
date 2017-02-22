---
title: "Analyse de la qualit&#233; d’un code manag&#233; &#224; l’aide de l’analyse du code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analyse du code, code managé"
  - "code managé, analyse"
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# Analyse de la qualit&#233; d’un code manag&#233; &#224; l’aide de l’analyse du code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez l'analyse du code dans Visual Studio pour découvrir d'éventuels problèmes dans votre code, tels que les accès aux données non sécurisés, les violations d'utilisation et les problèmes de conception.  L'analyse du code fonctionne sur les applications de base de données, .NET Framework et natives \(C et C\+\+\).  L'analyse du code pour le code managé organise des règles dans les *ensembles de règles* qui ciblent les problèmes d'encodage.  
  
## Tâches courantes  
  
|Tâches courantes|Contenu de support|  
|----------------------|------------------------|  
|**Apprendre en faisant :** apprenez les notions de base sur l'analyse du code en corrigeant des défauts dans une application .NET Framework simple.|-   [Procédure pas à pas : analyse du code managé pour les erreurs de code](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Configurer l'analyse du code pour un projet :** les règles pour le code managé sont organisées en ensembles de règles qui ciblent des zones spécifiques, telles que la sécurité et la conception.  Vous pouvez utiliser l'un des ensembles de règles standard Microsoft ou créer votre propre ensemble.|-   [Vue d’ensemble de l’analyse du code managé](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Utilisation d'ensembles de règles pour regrouper des règles d'analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Supprimer des avertissements à l'aide de l'attribut SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Exécuter l'analyse du code :** vous pouvez spécifier que l'analyse du code soit exécutée automatiquement chaque fois qu'une configuration de projet est générée, et vous pouvez exécuter l'analyse du code manuellement sur un projet.|-   [Comment : activer et désactiver l'analyse du code automatique](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md)<br />-   [Comment : exécuter l'analyse du code manuellement](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analyser des résultats d'analyse du code :** Les avertissements et les erreurs d'analyse sont listés dans la fenêtre d'analyse du code.  Vous pouvez choisir un avertissement ou un titre d'erreur pour afficher des informations supplémentaires sur l'avertissement, et afficher et mettre en surbrillance la ligne de code source qui a déclenché la règle.  Vous pouvez choisir l'identificateur d'avertissement pour afficher des informations détaillées dans la librairie MSDN qui incluent des informations et des exemples sur la façon de résoudre le problème.|-   [Procédure : afficher les défauts du code managé](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Analyse du code pour les avertissements liés au code managé](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Avertissements par CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Méthodes anonymes et analyse du code](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Intégrer l'analyse du code à votre cycle de vie de développement :** les stratégies d'archivage du [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] permettent aux équipes de développement de s'assurer que tous les archivages de code sont conformes à un ensemble commun de normes d'analyse du code.  La création d'un élément de travail pour une violation de la règle d'analyse du code est une procédure simple que vous pouvez exécuter dans la fenêtre Liste d'erreurs.|-   [Amélioration de la qualité du code avec des stratégies d’archivage de projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Comment : synchroniser des ensembles de règles applicables à des projets de code avec la stratégie d'archivage du projet d'équipe](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Comment : créer un élément de travail pour une erreur de code managé](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|