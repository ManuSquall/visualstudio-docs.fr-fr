---
title: "Utilisation d&#39;ensembles de r&#232;gles pour regrouper des r&#232;gles d&#39;analyse du code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.rulesets.learnmore"
helpviewer_keywords: 
  - "analyse du code, ensembles de règles"
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 36
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 36
---
# Utilisation d&#39;ensembles de r&#232;gles pour regrouper des r&#232;gles d&#39;analyse du code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous configurez l'analyse du code dans [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], ou [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], vous pouvez faire votre choix à partir d'une liste d' *ensembles de règle* provenant des standards Microsoft.  Un ensemble de règles est un regroupement logique de règles d'analyse du code qui identifient les problèmes ciblés et les conditions spécifiques.  Par exemple, vous pouvez appliquer un ensemble de règles qui est destiné au code d'analyse pour les APIs accessibles publiquement, ou vous pouvez appliquer un ensemble de règles qui inclut uniquement les règles minimales recommandées.  Vous pouvez également appliquer un ensemble de règles qui inclut toutes les règles.  
  
 Vous pouvez personnaliser un ensemble de règles en ajoutant, supprimant ou modifiant des règles qui doivent s'afficher dans la fenêtre **Liste d'erreurs** comme avertissements ou erreurs.  Les ensembles de règles personnalisés peuvent répondre à un besoin de votre environnement de développement spécifique.  Lorsque vous personnalisez un ensemble de règles, la page de l'ensemble de règles propose des outils de recherche et de filtrage pour vous aider dans le processus.  
  
## Tâches courantes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Apprendre par la pratique :** utilisez les outils d'analyse du code pour spécifier un ensemble de règles personnalisé afin de rechercher et résoudre les problèmes dans une application .NET Framework simple.|-   [Procédure pas à pas : configuration et utilisation d’un ensemble de règles personnalisé](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**Configurer l'analyse du code pour un projet :** choisissez un ensemble de règles existant pour un projet, un site Web ou une solution.|-   [Procédure : configurer l’analyse du code pour un projet de code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [Utilisation des ensembles de règles pour spécifier les règles C\+\+ à exécuter](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Comment : configurer l'analyse du code pour une application Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Comment : spécifier des ensembles de règles pour plusieurs projets dans une solution](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**Personnaliser un ensemble de règles :** spécifiez les règles à appliquer à votre projet.|-   [Création d'ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**Comprendre les ensembles de règles intégrés :** consultez les règles d'analyse du code qui composent les ensembles de règles intégrés.|-   [Référence d’ensemble de règles d’analyse du code](../code-quality/code-analysis-rule-set-reference.md)|  
|**Intégrer l'analyse du code dans Team Foundation Server :**les stratégies d'archivage [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] permettent aux équipes de développement de s'assurer que tous les archivages de code sont conformes à un ensemble commun de normes d'analyse du code.|-   [Comment : synchroniser des ensembles de règles applicables à des projets de code avec la stratégie d'archivage du projet d'équipe](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|